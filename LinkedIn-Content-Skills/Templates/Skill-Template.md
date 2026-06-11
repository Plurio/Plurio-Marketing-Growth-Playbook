# Claude Code Skill — Template

> How to create your own skill for Claude Code.
> A skill = a file with instructions that Claude executes via a `/slash-command`.

---

## What Is a Claude Code Skill

A skill is a markdown file with:
1. **Frontmatter** (YAML) — metadata: name, description, allowed tools
2. **Pipeline** — step-by-step instructions on what to do

Claude Code reads this file and executes the steps sequentially. It's not code — it's methodology in a format the AI can reproduce consistently.

---

## File Structure

```
your-project/
├── .claude/
│   └── skills/
│       ├── create-post/
│       │   └── SKILL.md        ← skill invoked via /create-post
│       ├── validate-content/
│       │   └── SKILL.md        ← /validate-content
│       └── update-profile/
│           └── SKILL.md        ← /update-profile
├── CLAUDE.md                    ← routing (which skill to invoke when)
└── Skills/                      ← reference files (knowledge base)
```

**Important:** the skill's directory name = the command name. `create-post/SKILL.md` → invoked via `/create-post`.

---

## Frontmatter — Fields

```yaml
---
name: create-post
description: "Creates a post for an author via a pipeline using their DIP and current trends"
disable-model-invocation: false
allowed-tools: Read, Grep, Glob, Write, Edit
---
```

| Field | Required | Description |
|-------|----------|-------------|
| `name` | Yes | Skill name (lowercase-hyphenated) |
| `description` | Yes | What it does — Claude uses this for routing |
| `disable-model-invocation` | No | `true` = skill is NOT auto-invoked, only explicitly via /command |
| `context` | No | `fork` = runs in an isolated context (for validators) |
| `allowed-tools` | Yes | Which tools are available to the skill |
| `argument-hint` | No | Argument hint: `[Author] [topic]` |

### Available Tools (allowed-tools)

| Tool | Purpose |
|------|---------|
| `Read` | Reading files |
| `Write` | Creating new files |
| `Edit` | Editing existing files |
| `Grep` | Searching file contents |
| `Glob` | Searching for files by pattern |
| `Bash` | Running shell commands (can be scoped: `Bash(python *)`) |
| `Skill` | Calling other skills (can be scoped: `Skill(validate-content *)`) |
| `WebSearch` | Searching the web |
| `Agent` | Spawning subtasks |

---

## SKILL TEMPLATE

```yaml
---
name: [skill-name]
description: "[What the skill does — 1-2 sentences]"
disable-model-invocation: false
allowed-tools: Read, Grep, Glob, Write, Edit
argument-hint: "[Author] [topic]"
---
```

```markdown
# [Skill Name]

## When to Use
[1-2 sentences — in which situations to invoke this skill]

## Required Files to Load

1. **[Name]** (required):
   `path/to/reference-file.md`

2. **[Name]** (required):
   `path/to/another-file.md`

3. **[Name]** (recommended):
   `path/to/optional-file.md`

## Pipeline

### Step 1: [Step name]
[Concrete instructions — what to read, what to extract, what to check]

### Step 2: [Step name]
[Instructions]

### Step 3: [Step name]
[Instructions]

### Step N: Save the Output
Save to: `path/to/output/YYYY-MM-DD-[slug].md`

Format:
- [description of the output format]

## Pre-Completion Checklist
- [ ] [check 1]
- [ ] [check 2]
- [ ] [check 3]

## Related Skills
- Run after this skill: `/validate-content`
- If a new profile is needed: `/create-profile`
```

---

## Skill Patterns

### Pattern 1: Worker (does the work)

```yaml
disable-model-invocation: false
```
Direct execution. Examples: `/check-facts`, `/detect-ai`, `/create-post`.

### Pattern 2: Orchestrator (coordinates)

```yaml
disable-model-invocation: true
allowed-tools: Read, Skill
```
Calls other skills in a chain. Doesn't do the work itself. Example: `/validate-content` calls 5 validators.

### Pattern 3: Validator (checks in isolation)

```yaml
context: fork
```
Runs in an isolated context. Doesn't affect the main conversation. Ideal for checks.

---

## Example: Minimal Skill for Creating a Post

```yaml
---
name: create-post
description: "Creates a post for an author. Usage: /create-post [Author] [topic]"
disable-model-invocation: false
allowed-tools: Read, Grep, Glob, Write, Edit, Skill(validate-content *)
argument-hint: "[Author] [topic]"
---
```

```markdown
# Create Post

## Required Files

1. **Author DIP** (required):
   `Skills/01-Identity-Profiles/[Author]-DIP.md`

2. **Algorithm Intelligence** (required):
   `Skills/02-Platform-Algorithm/Algorithm-Intelligence.md`

3. **Current Trends** (recommended):
   `Skills/03-Trends/Current-Trends.md`

## Pipeline

### Step 1: Load context
Read the author's DIP, Algorithm Intelligence, and Current Trends.

### Step 2: Analyze raw material
If the user provided a transcript/text — extract the key message.
If only a topic — search for relevant material in the author's sources.

### Step 3: Pick angle and format
Based on DIP Viral Angles + trends, choose:
- Angle (contrarian, case study, framework, behind the scenes)
- Format (text, carousel, video)

### Step 4: Writing
- Hook: first 140 characters — must stop the scroll
- Body: short paragraphs, specifics, numbers
- CTA: a specific question or action
- Tone: strictly per the DIP

### Step 5: Self-check
- [ ] Length 1200-1800 characters?
- [ ] First person (I/my)?
- [ ] No generic phrases?
- [ ] Hook stops scrolling?
- [ ] CTA is specific?

### Step 6: Save
Save to `Posted/[Author]/YYYY-MM-DD-[slug].md`

### Step 7: Validate
Run `/validate-content` on the created file.
```

---

## CLAUDE.md — Routing

So Claude Code knows which skill to invoke when, add the following to CLAUDE.md:

```markdown
## Routing

| User request | Skill |
|--------------|-------|
| "Create a post for [Author]" | `/create-post [Author] [topic]` |
| "Validate the content" | `/validate-content [file]` |
| "Update the profile for [Author]" | `/update-profile [Author]` |
```
