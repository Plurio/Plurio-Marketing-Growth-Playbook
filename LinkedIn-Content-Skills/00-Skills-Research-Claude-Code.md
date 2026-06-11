# Skills in Claude Code: full research

> **Purpose of this document:** Understand what Skills are in Claude Code, how to build them, and how Claude works with them. Written so it can be explained to someone else.
> **Date:** 2026-02-26
> **Sources:** 7 independent (official documentation + 6 practitioner authors)

---

## 1. What Skills are (in plain language)

**Skills** are extensions that teach Claude Code new capabilities or automate repetitive workflows.

In the simplest terms: you write a markdown file with instructions → Claude Code finds it → and starts applying those instructions when the task matches. Or you invoke the skill manually with `/skill-name`.

**Analogy:** a skill is like a job description for an employee. You describe once how a specific job should be done (writing posts, reviewing PRs, deploying), and from then on the employee (Claude) follows those instructions every time that task comes up.

**What skills let you do:**
- Create your own `/slash commands` (e.g., `/create-post`, `/review-pr`, `/deploy`)
- Package repetitive workflows into a reusable format
- Give Claude reference knowledge (style guides, conventions, patterns)
- Run tasks in isolated subprocesses (subagents)
- Attach supporting files (templates, examples, scripts)

> **Historical note:** there used to be separate "slash commands" (files in `.claude/commands/`) and "skills" (files in `.claude/skills/`). Anthropic has now merged them — both formats still work, but **skills** are the recommended approach because they support more features.
> — [Official Anthropic documentation](https://code.claude.com/docs/en/skills)

---

## 2. Anatomy of a skill

### Minimal structure

```
my-skill/
└── SKILL.md          ← the only required file
```

### Extended structure

```
my-skill/
├── SKILL.md           # Main instructions (required)
├── reference.md       # Detailed documentation (loaded on demand)
├── examples/
│   └── sample.md      # Examples of expected output
└── scripts/
    └── helper.py      # A script Claude can run
```

### Anatomy of SKILL.md

The file consists of two parts:

```yaml
---
# PART 1: YAML Frontmatter (configuration)
name: create-post
description: Creates a LinkedIn post for an author. Use when asked to write a post.
allowed-tools: Read, Grep, Glob
---

# PART 2: Markdown content (instructions)

Create a LinkedIn post for author $ARGUMENTS:

1. Load the author's DIP
2. Identify the topic and angle
3. Choose a format and hook
4. Write the post
5. Verify against the checklist
```

### All frontmatter fields (reference)

| Field | Required? | What it does |
|------|-------------|------------|
| `name` | No | Skill name = name of the `/slash command`. Lowercase letters, digits, hyphens only. Max 64 characters. If omitted — the folder name is used |
| `description` | **Recommended** | What the skill does and when to use it. **This is the key field** — Claude uses it to decide when to apply the skill automatically |
| `argument-hint` | No | Autocomplete hint. Example: `[author-name]` or `[file] [format]` |
| `disable-model-invocation` | No | `true` = only you can invoke it (Claude won't invoke it on its own). For risky operations: deploy, commit, sending messages |
| `user-invocable` | No | `false` = the skill does NOT appear in the `/` menu. Only Claude can use it. For background knowledge |
| `allowed-tools` | No | Which tools Claude can use without asking for permission. Example: `Read, Grep, Bash(git *)` |
| `model` | No | A specific model for this skill |
| `context` | No | `fork` = run in an isolated subagent (separate context) |
| `agent` | No | Subagent type when `context: fork` (e.g., `Explore`, `Plan`, `general-purpose`) |

> **Source:** [Official docs — Frontmatter Reference](https://code.claude.com/docs/en/skills)

---

## 3. Where skills live (3 levels)

| Level | Path | Who sees it |
|---------|------|-----------|
| **Enterprise** | `/Library/Application Support/ClaudeCode/skills/` (macOS) | All users in the organization |
| **Personal** | `~/.claude/skills/<skill-name>/SKILL.md` | All your projects |
| **Project** | `.claude/skills/<skill-name>/SKILL.md` | This project only |

**Priority on name conflict:** Enterprise > Personal > Project.

**Nested-folder auto-discovery:** if you work in `packages/frontend/`, Claude Code automatically picks up skills in `packages/frontend/.claude/skills/`. This supports monorepo structures.

**Live updates:** skills in `.claude/skills/` are picked up during the session without a restart. You can edit and test on the fly.

> **Practical tip from David Taylor** (Cloud Artisan): keep project skills in Git — automatic version control, team access, ability to roll back changes.
> — [Cloud Artisan: Claude Code Tips & Tricks](https://cloudartisan.com/posts/2025-04-14-claude-code-tips-slash-commands/)

---

## 4. How Claude Code interacts with skills

This is the key part — understanding exactly how Claude finds, loads, and uses skills.

### 4.1. Discovery

```
At the start of a Claude Code session:
  1. Scans ~/.claude/skills/         → personal skills
  2. Scans .claude/skills/           → project skills
  3. Scans nested .claude/skills/    → monorepo skills
  4. Loads ONLY each skill's description into context
     (full content is loaded ONLY on invocation)
```

### 4.2. Two invocation modes

**Automatic (Claude decides):**
- Claude sees the descriptions of all available skills
- When your request matches a description — Claude loads the full content and follows the instructions
- Example: the description says "Use when explaining how code works" → you ask "How does this code work?" → Claude automatically activates the skill

**Manual (you invoke it):**
```
/skill-name arg1 arg2
```

> **Honest assessment from Product Talk** (Product Talk): "Claude is supposed to recognize when to invoke them. But I haven't had much luck with this." She prefers slash commands for predictability of invocation.
> — [Product Talk: How to Use Claude Code](https://www.producttalk.org/how-to-use-claude-code-features/)

> **What this means:** the description should be written as precisely as possible. The more specific the description — the more reliable the auto-trigger. For critical workflows, prefer manual invocation (`/skill-name`).

### 4.3. What happens on invocation (sequence)

```
1. User (or Claude) invokes the skill
2. Claude Code reads SKILL.md
3. YAML frontmatter is parsed (settings)
4. Substitutions are performed ($ARGUMENTS, $0, $1...)
5. Dynamic commands are executed (!`command`)
6. The resulting markdown is sent to Claude (or the subagent if context: fork)
7. Claude follows the instructions
```

### 4.4. String Substitutions

| Variable | What gets substituted |
|------------|------------------|
| `$ARGUMENTS` | All arguments passed at invocation |
| `$ARGUMENTS[0]`, `$ARGUMENTS[1]` | A specific argument by index |
| `$0`, `$1`, `$2` | Shorthand for `$ARGUMENTS[N]` |
| `${CLAUDE_SESSION_ID}` | Current session ID |

**Example:**
```yaml
---
name: create-post
description: Creates a LinkedIn post for an author
---

Create a post for author $0 on the topic $1.
```

Invocation: `/create-post Seva AI-agents` → Claude receives: "Create a post for author Seva on the topic AI-agents."

### 4.5. Dynamic context (!`command`)

Skills can run shell commands **BEFORE** the content reaches Claude. This is preprocessing — the commands execute and the result is substituted into the text.

```yaml
---
name: pr-summary
description: Pull request summary
---

## PR Context
- Diff: !`gh pr diff`
- Comments: !`gh pr view --comments`
- Changed files: !`gh pr diff --name-only`

## Task
Write a summary of this PR...
```

Claude receives not the commands but their **results** — the actual diff, the actual comments.

> **Source:** [Official docs — Inject dynamic context](https://code.claude.com/docs/en/skills)

---

## 5. Two types of skills: Reference vs Task

This is a fundamental distinction that shapes how you design a skill.

### Reference Skills (knowledge)

**What it is:** context, conventions, style guides — knowledge that Claude applies to current work.

**When to use:** when you need Claude to *know* something while working, rather than performing a concrete action.

**Example:**
```yaml
---
name: api-conventions
description: API design patterns for this project
---

When writing API endpoints:
- Use RESTful naming
- Return a single error format
- Include request validation
```

**Characteristics:**
- Usually invoked automatically by Claude
- Works inline (in the main conversation context)
- No specific "output" — it just shapes the quality of the work

### Task Skills (actions)

**What it is:** step-by-step instructions for a specific task.

**When to use:** when you need Claude to *do* something concrete.

**Example:**
```yaml
---
name: deploy
description: Deploy to production
disable-model-invocation: true
---

Deploy the app:
1. Run the tests
2. Build the artifact
3. Push to deploy
4. Verify the deploy succeeded
```

**Characteristics:**
- More often invoked manually (`/deploy`)
- May run in an isolated subagent (`context: fork`)
- Has a specific expected outcome

> **Insight from External engineer:** "The difference is mostly UX + packaging: slash commands are what you can run manually from the terminal via `/command`; skills are structured, auto-discovered capabilities." He recommends using subagents for research-heavy tasks so the main context doesn't get polluted.
> — [alexop.dev: Claude Code Customization Guide](https://alexop.dev/posts/claude-code-customization-guide-claudemd-skills-subagents/)

---

## 6. Advanced patterns

### 6.1. Subagents (`context: fork`)

When a skill runs with `context: fork`, it works **in an isolated context** — a separate Claude that doesn't see your current conversation. The result is returned as a summary.

```yaml
---
name: deep-research
description: Deep research on a topic
context: fork
agent: Explore
---

Research $ARGUMENTS:
1. Find relevant files via Glob and Grep
2. Read and analyze the code
3. Return a summary with concrete file references
```

**When to use fork:**
- Research tasks (heavy file reading that would pollute the main context)
- Heavy workflows that need a "clean slate"
- Parallel tasks

> **External engineer:** "Subagents keep your main context clean — in plan mode, Claude Code will typically delegate repo scanning to an Explore-style subagent so your main thread doesn't balloon."

### 6.2. Invocation control

| Setting | You can invoke | Claude can invoke | When to use |
|-----------|-------------------|---------------------|-------------------|
| Default | Yes | Yes | Most skills |
| `disable-model-invocation: true` | Yes | **No** | Risky operations (deploy, commit, sending messages) |
| `user-invocable: false` | **No** | Yes | Background knowledge (legacy-system-context) |

### 6.3. Scripts inside skills

Skills can contain executable scripts. The official docs include an example skill `codebase-visualizer` that runs a Python script to generate an interactive HTML codebase visualization.

```
codebase-visualizer/
├── SKILL.md              # Instructions for Claude
└── scripts/
    └── visualize.py      # Python script that Claude runs
```

### 6.4. Hierarchical organization

> **David Taylor** (Cloud Artisan) organizes skills hierarchically by function using subdirectories. For example: `project:site:preview`, `project:posts:publish`. This creates an intuitive namespace as the command collection grows.
> — [Cloud Artisan: Claude Code Tips](https://cloudartisan.com/posts/2025-04-14-claude-code-tips-slash-commands/)

---

## 7. What practitioners say

### Product Talk (Product Talk)
**Who:** product coach, author of Continuous Discovery Habits
**Experience:** uses slash commands for /headlines, /seo, /today, /competitive-research
**Key takeaway:** "Skills are supposed to be auto-recognized by Claude, but that doesn't always work for me. I prefer slash commands for predictability — you have full control over when something fires."
**Practice:** instead of skills that Claude invokes itself, she uses slash commands that she invokes herself
→ [Source](https://www.producttalk.org/how-to-use-claude-code-features/)

### Steve Sewell (CEO of Builder.io)
**Who:** CEO of Builder.io, former Cursor power user, switched to Claude Code
**Experience:** customized his PR review prompt, works with 18,000+ line files
**Key takeaway:** dialed in his review prompt: "Please review this pull request and look for bugs and security issues. Only report on bugs and potential vulnerabilities. Be concise." The default config was too verbose
**Practice:** runs multiple Claude Code instances in parallel across different IDE panels
→ [Source](https://www.builder.io/blog/claude-code)

### External engineer (developer)
**Who:** developer, author of a detailed customization guide
**Experience:** built an architectural pyramid: CLAUDE.md → Slash Commands → Skills → Subagents
**Key takeaway:** each mechanism has its own job:

| Mechanism | Main context | Separate window | Manual invocation |
|----------|------------------|----------------|-------------|
| CLAUDE.md | yes | no | no |
| Slash Command | yes | no | yes |
| Skill | yes | no | no |
| Subagent | no | yes | partial |

**Practice:** for reading-heavy tasks (documentation, research) he uses subagents so the main context doesn't balloon
→ [Source](https://alexop.dev/posts/claude-code-customization-guide-claudemd-skills-subagents/)

### David Taylor (Cloud Artisan)
**Who:** DevOps engineer, blogger
**Experience:** organizes skills hierarchically, stores them in Git for team access
**Key takeaway:** "Keeping commands in Git gives you automatic change history, team access, an easy improvement workflow, and the ability to roll back."
**Practice:** builds a help command (`/project:view_commands`) that documents all available options
→ [Source](https://cloudartisan.com/posts/2025-04-14-claude-code-tips-slash-commands/)

### BioErrorLog (developer, Tech Blog)
**Who:** technical blogger
**Experience:** step-by-step examples from simple to advanced
**Key takeaway:** frontmatter lets you finely tune which tools a skill has access to. For example, `allowed-tools: Bash(git status:*), Bash(git diff:*)` — the skill can only run specific git commands
**Practice:** uses the `!` syntax to inject shell command output directly into the prompt
→ [Source](https://en.bioerrorlog.work/entry/claude-code-custom-slash-command)

---

## 8. How to build a skill for a task (step-by-step guide)

### Step 1: Determine the type

| Question | Reference | Task |
|--------|-----------|------|
| Should Claude *know* this or *do* this? | Know | Do |
| Is there a specific step-by-step process? | No | Yes |
| Is a specific output required? | No | Yes |
| Example | Style guide, ICP, conventions | Create a post, deploy, review |

### Step 2: Determine scope

| Question | Personal | Project |
|--------|----------|---------|
| Needed across all projects? | Yes | No |
| Needed by the team? | No | Yes (via Git) |
| Contains secrets? | Yes (not in Git) | No |

### Step 3: Create the structure

```bash
# Personal
mkdir -p ~/.claude/skills/my-skill

# Project
mkdir -p .claude/skills/my-skill
```

### Step 4: Write the description (THE MOST IMPORTANT STEP)

The description is what Claude uses to decide when to apply the skill automatically. A bad description = the skill doesn't fire, or fires in the wrong situation.

**Bad:**
```yaml
description: Helps with posts
```

**Good:**
```yaml
description: Creates a LinkedIn post for a team author. Use when the user asks to write, create, or make a post for LinkedIn, or says "turn this into a post".
```

**Rules:**
- Specific keywords the user is likely to actually say
- State the context ("for LinkedIn", "for an author")
- State trigger phrases ("when the user asks...")

### Step 5: Write the instructions

```yaml
---
name: create-post
description: Creates a LinkedIn post for a team author...
---

## Required steps

1. Load the author's DIP from Skills/01-Digital-Identity-Profiles/
2. Load Algorithm-Intelligence.md
3. Identify the topic and angle
4. Pick a format and hook per Hook-Pattern-Library.md
5. Write the post in the author's voice (FIRST PERSON)
6. Verify against the Post-Creation-Engine.md checklist
7. Save to Posted/[Author]/YYYY-MM-DD-[slug].md
```

### Step 6: Add supporting files (if needed)

Keep SKILL.md under 500 lines. Detailed docs go in separate files.

```
create-post/
├── SKILL.md              # Main instructions
├── checklist.md          # Quality checklist
├── examples/
│   └── good-post.md      # Example of a good post
└── templates/
    └── post-template.md  # Post file template
```

### Step 7: Configure the frontmatter

| Scenario | What to add |
|----------|-------------|
| Risky operation (deploy, commit) | `disable-model-invocation: true` |
| Heavy research | `context: fork` + `agent: Explore` |
| Only certain tools | `allowed-tools: Read, Grep, Glob` |
| Background knowledge | `user-invocable: false` |

### Step 8: Test it

1. Manually: `/create-post Seva` — does it work?
2. Automatically: "Write a post for Seva about AI agents" — does it trigger?
3. Check `/context` — has the skill's character budget been exceeded?

---

## 9. Your current LinkedIn skills: analysis

### What exists today

Your LinkedIn Content Machine is **7 modules** in `Content/LinkedIn/Skills/`:

| Module | Folder | Type | Status |
|--------|-------|-----|--------|
| Digital Identity Profiles | `01-Digital-Identity-Profiles/` | Reference | 5 DIPs (2 production, 3 partial) |
| LinkedIn Algorithm | `02-LinkedIn-Algorithm/` | Reference | 3 files, up to date |
| Viral Trends | `03-Viral-Trends/` | Reference | 4 files |
| Post Creation Engine | `04-Post-Creation-Engine/` | Task | Main pipeline, 4 files |
| Format Testing | `05-Format-Testing/` | Reference + Task | 3 files |
| Comments Engine | `06-Comments-Engine/` | Task | 1 file (13KB) |
| Auto-Update | `07-Auto-Update/` | Task | Weekly workflow |

### Key insight

This is **NOT** Claude Code Skills in the technical sense. It's documentation routed through `CLAUDE.md`. There are no `SKILL.md` files, no YAML frontmatter, no auto-discovery.

**How it works today:**
```
CLAUDE.md (routing table)
  → User says "create a post"
  → Claude reads the table in CLAUDE.md
  → Loads the required files manually
  → Follows the instructions
```

**How it could work:**
```
.claude/skills/create-post/SKILL.md (auto-discovery)
  → User says "create a post"
  → Claude automatically recognizes the task from the description
  → Loads the full skill content
  → Follows the instructions
  → Supporting files are loaded via references from SKILL.md
```

### What this gives you

| Aspect | Today (CLAUDE.md routing) | With Claude Code Skills |
|--------|---------------------------|---------------------|
| Discovery | Manual (Claude searches the table) | Automatic (by description) |
| Manual invocation | No | `/create-post Seva` |
| Load control | None (all in context or nothing) | Description only → full content on invocation |
| Supporting files | All in one place | Structured folder |
| Subagents | Via CLAUDE.md instructions | Built-in `context: fork` |
| Shared via Git | Yes | Yes |

### Recommendation

**The current system works.** CLAUDE.md routing is a valid approach, especially given that Product Talk also prefers predictable manual invocation. But if you want to level it up:

1. **Quick win:** add `disable-model-invocation: true` skills for the main workflows (`/create-post`, `/create-comment`, `/update-dip`) — this gives you manual invocation via `/` without losing the existing CLAUDE.md routing
2. **Mid-tier win:** move heavy research (weekly update, DIP creation) into `context: fork` skills — they won't pollute the main context
3. **Full migration:** convert all 7 modules into full Claude Code Skills with SKILL.md and supporting files

---

## 10. Sources

| # | Author / Organization | Article | URL |
|---|-------------------|--------|-----|
| 1 | **Anthropic** (official docs) | Extend Claude with skills | https://code.claude.com/docs/en/skills |
| 2 | **Product Talk** (Product Talk) | How to Use Claude Code: A Guide to Slash Commands, Agents, Skills, and Plug-ins | https://www.producttalk.org/how-to-use-claude-code-features/ |
| 3 | **Steve Sewell** (Builder.io CEO) | How I use Claude Code (+ my best tips) | https://www.builder.io/blog/claude-code |
| 4 | **External engineer** (developer) | Claude Code Customization: CLAUDE.md, Slash Commands, Skills, and Subagents | https://alexop.dev/posts/claude-code-customization-guide-claudemd-skills-subagents/ |
| 5 | **BioErrorLog** (Tech Blog) | How to Create Custom Slash Commands in Claude Code | https://en.bioerrorlog.work/entry/claude-code-custom-slash-command |
| 6 | **David Taylor** (Cloud Artisan) | Claude Code Tips & Tricks: Custom Slash Commands | https://cloudartisan.com/posts/2025-04-14-claude-code-tips-slash-commands/ |
| 7 | **SFEIR Institute** | Custom commands and skills — Tutorial | https://institute.sfeir.com/en/claude-code/claude-code-custom-commands-and-skills/ |
