# LinkedIn Content Machine — Skills Guide & Workflow

> **Purpose:** Complete instructions for the LinkedIn content creation system built on Claude Code Skills. For onboarding new contributors and as a reference for the team.
> **Date:** 2026-02-26
> **Version:** 1.0
> **Related documents:**
> - Technical research: `00-Skills-Research-Claude-Code.md`
> - Routing: `.claude/CLAUDE.md` and `Content/LinkedIn/CLAUDE.md`

---

## 1. What this is and why

LinkedIn Content Machine is the team's content creation system. Each contributor (Seva, Kirill) has their own Digital Identity Profile (DIP), and the system produces posts on their behalf while preserving tone of voice, expertise, and thinking style.

The system runs on **Claude Code Skills** — automated workflows invoked by `/slash commands` in the Claude chat.

### Why Skills, not just documentation

Before Skills: Claude read documentation through routing in CLAUDE.md → quality depended on what Claude decided to load.

With Skills:
- **Each workflow = `/command`** → invoked explicitly, predictably
- **Validation agents** → automatic checks after content creation
- **Isolated subagents** → each check runs independently, doesn't get confused by context
- **Reusability** → one skill is invoked from another (`/create-post` → automatically → `/validate-post`)

> **Full research on what Skills are in Claude Code, how they're structured, and how to build them:**
> `00-Skills-Research-Claude-Code.md` (7 sources, including Anthropic's official documentation)

---

## 2. Architecture: 3 layers

```
┌─────────────────────────────────────────────────────────────┐
│  LAYER 1: REFERENCE (knowledge)                             │
│  Loaded automatically via CLAUDE.md routing                  │
│                                                              │
│  01-Digital-Identity-Profiles/ → DIP for each author         │
│  02-LinkedIn-Algorithm/        → algorithm, formats, timing  │
│  03-Viral-Trends/              → trends, hooks, anti-patterns│
│  05-Format-Testing/            → format catalog              │
│  06-Comments-Engine/           → comments engine             │
│  07-Auto-Update/               → weekly refresh              │
├─────────────────────────────────────────────────────────────┤
│  LAYER 2: TASK SKILLS (actions — triggered via /command)     │
│                                                              │
│  /create-post    → 8-step post creation pipeline             │
│  /create-comment → comment creation                          │
│  /update-dip     → update an author's profile                │
├─────────────────────────────────────────────────────────────┤
│  LAYER 3: VALIDATION AGENTS (checks — context: fork)         │
│  Run after creation, work in isolation                       │
│                                                              │
│  /check-facts    → fact-checking + logical integrity         │
│  /check-generic  → generic phrasing, AI language, repeats    │
│  /check-sources  → provenance map for every statement        │
│  /validate-post  → master: all 3 checks + final checklist    │
└─────────────────────────────────────────────────────────────┘
```

**Layer 1 (Reference)** is knowledge. Claude loads it automatically when needed. It lives in `Content/LinkedIn/Skills/`.

**Layer 2 (Task Skills)** is action. You invoke them with `/create-post Seva "topic"`. They live in `.claude/skills/`.

**Layer 3 (Validation)** is the checks. Triggered automatically after a post is created (or manually). Each validator runs in an isolated subagent (`context: fork`) so the main context stays clean.

---

## 3. Folder structure

### Reference Layer: `Content/LinkedIn/Skills/`

```
Skills/
├── 00-Skills-Research-Claude-Code.md   ← research on Claude Code Skills
├── 00-LinkedIn-Skills-Guide.md         ← this document
├── 01-Digital-Identity-Profiles/
│   ├── Seva-Ustinov-DIP.md             ← v1.0
│   ├── Kirill-Kasimskiy-DIP.md         ← v1.0
│   ├── _DIP-Template.md
│   ├── _DIP-Creation-Workflow.md
│   ├── _DIP-Update-Workflow.md
│   └── _Sources/                       ← raw source material for DIPs
├── 02-LinkedIn-Algorithm/
│   ├── Algorithm-Intelligence.md       ← 360Brew model, 8 factors
│   ├── Format-Performance-Data.md      ← format benchmarks
│   └── Posting-Time-Guidelines.md      ← optimal posting times
├── 03-Viral-Trends/
│   ├── Current-Trends.md               ← current trends
│   ├── Hook-Pattern-Library.md         ← hook library
│   ├── Anti-Patterns.md                ← what NOT to do
│   └── Viral-Trends-Watchlist.md       ← trend monitoring
├── 04-Post-Creation-Engine/
│   ├── Post-Creation-Engine.md         ← main pipeline (8 steps)
│   ├── Voice-Input-Workflow.md         ← voice input processing
│   ├── Post-Template.md                ← post file template
│   └── Benchmark-Validation-System.md  ← number verification
├── 05-Format-Testing/
│   ├── Format-Catalog.md               ← all available formats
│   ├── Performance-Log.md              ← format results
│   └── Experiment-Backlog.md           ← experiment backlog
├── 06-Comments-Engine/
│   └── Comments-Engine.md              ← full comments engine
└── 07-Auto-Update/
    └── Weekly-Update-Workflow.md        ← weekly system refresh
```

### Task + Validation Layer: `.claude/skills/`

```
.claude/skills/
├── create-post/
│   └── SKILL.md       ← /create-post — orchestrates pipeline + auto-validation
├── create-comment/
│   └── SKILL.md       ← /create-comment — comment creation
├── update-dip/
│   └── SKILL.md       ← /update-dip — DIP update
├── check-facts/
│   └── SKILL.md       ← /check-facts — fact-checking (context: fork)
├── check-generic/
│   └── SKILL.md       ← /check-generic — generic/repeats (context: fork)
├── check-sources/
│   └── SKILL.md       ← /check-sources — source map (context: fork)
└── validate-post/
    └── SKILL.md       ← /validate-post — master validator (all 3 + checklist)
```

### Published Posts: `Content/LinkedIn/Posted/`

```
Posted/
├── Seva/        ← 36+ posts
├── Kirill/      ← 7+ posts
├── Ella/        ← 2+ posts
└── Denis/       ← 1 test post
```

---

## 4. All slash commands

### Task Skills

| Command | What it does | When to use | What it loads |
|---------|------------|-------------------|---------------|
| `/create-post [Author] [topic]` | Creates a post via the 8-step pipeline, saves it to Posted/, automatically triggers validation | "Write a post for Seva about..." or "Turn this into a post" | DIP, Post-Creation-Engine, Algorithm, Trends, Hooks |
| `/create-comment [Author]` | Creates a comment on the author's behalf | "Write a comment from Kirill on this post" | DIP, Comments-Engine |
| `/update-dip [Author]` | Updates the author's DIP with new data | After a new transcript, feedback, or whenever new content needs to be added | DIP, _DIP-Update-Workflow |

### Validation Agents

| Command | What it checks | When to use |
|---------|--------------|-------------------|
| `/validate-post [file]` | EVERYTHING: facts + generic + sources + final checklist (character count, format rotation, cluster, hook, anti-patterns, mobile) | After creating a post. After any edits. On any existing post |
| `/check-facts [file]` | Factual accuracy. Catches compilations from multiple sources, verifies logical integrity | When the post is based on multiple transcripts/sources |
| `/check-generic [file]` | Generic phrasing, AI language, repeated hooks/markers/CTAs from the last 10 posts, tone alignment with the DIP | When you want to check writing quality or "does it sound like the author" |
| `/check-sources [file]` | Transparency: where each statement came from, verbatim source quotes, compilations, unused source_refs | When you need to show provenance for every claim |

### Pipeline: how the skills chain

```
/create-post Seva "topic"
    ↓
  Steps 1-7: post creation
    ↓
  Save to Posted/Seva/YYYY-MM-DD-slug.md
    ↓
  Automatically: /validate-post [file]
    ↓
  ┌─ /check-facts    (subagent, isolated)
  ├─ /check-generic   (subagent, isolated)
  ├─ /check-sources   (subagent, isolated)
  └─ Final checklist (character count, format, cluster, hook, anti-patterns)
    ↓
  Summary report → user
    ↓
  Edits based on recommendations
    ↓
  /validate-post [file]  ← manual re-run after edits
    ↓
  New report
    ↓
  Publish
    ↓
  Feedback → /update-dip [Author]
```

---

## 5. Workflow: Post creation (full cycle)

### Step 1: Launch

```
/create-post Seva "post topic or source link"
```

Or simply say: "Write a post for Seva about [topic]" — Claude will pick up the skill automatically.

If there's voice input (audio/transcript): Claude first runs it through the Voice-Input-Workflow, then launches the pipeline.

### Step 2: Pipeline (automatic)

Claude executes the 8 steps from Post-Creation-Engine:
1. Loads the author's DIP
2. Extracts the core message
3. Picks an angle + format
4. Writes the post (hook, body, CTA)
5. Basic validation
6. Formats the output (text + alternative hooks + recommendations)
7. Saves to `Posted/[Author]/YYYY-MM-DD-[slug].md`
8. Triggers `/validate-post`

### Step 3: Validation (automatic)

`/validate-post` runs in parallel:
- `/check-facts` — are all statements backed by sources? Any compilations that distort context?
- `/check-generic` — any AI language, clichés, or repeats from the last 10 posts?
- `/check-sources` — where does each idea come from? Verbatim quotes from the originals

Plus the final checklist:
- Character count: 1,200–1,800 optimal, 3,000 max
- Format: does it repeat the last 3 posts?
- Cluster: not 5+ posts in a row in the same cluster?
- Hook: doesn't duplicate a recent one?
- Anti-patterns: no engagement bait? No bro-etry? No link in the first 300 characters?
- Mobile: paragraphs no longer than 3 lines?

### Step 4: Edits

Based on validation results — make changes. Overwrite the file (do NOT create `-v2`).

### Step 5: Re-validation

```
/validate-post Posted/Seva/2026-03-01-my-post.md
```

Re-check after edits. Can be run as many times as needed.

### Step 6: Publish and feedback

After publishing and getting feedback:

```
/update-dip Seva
```

Always log into the DIP → section "FEEDBACK LOG & LEARNINGS":
- What worked / didn't
- Engagement metrics
- Takeaways for future posts

---

## 6. Workflow: Comments

### Current skill

```
/create-comment Kirill
```

Creates a comment per the rules in Comments-Engine.md:
- 3 types: reply to own post / comment on someone else's post / start a discussion
- Minimum 15 words (2.5x algorithm weight)
- Specifics from the DIP Stories Bank
- Never: "Great post!", "Love this!", "Totally agree!" — generic, zero value

### Future skills (TODO)

When ready:

| Skill | Purpose | When to trigger |
|-------|-----------|----------------|
| `/comment-own-post [Author] [post]` | First comment on your own post: link, extra context, discussion question | Immediately after publishing (first 30 seconds) |
| `/comment-others [Author] [post-url]` | Comment on someone else's post: networking, thought leadership, positioning | Daily routine (3–5 comments per day) |
| `/amplify [Author] [post]` | Cross-team amplification: team coordination to comment on a colleague's post | Within 10–30 minutes after publishing |
| `/comment-reply [Author] [comment]` | Reply to an incoming comment on your own post | First 30 minutes after publishing (algorithm-critical) |

### Comments workflow at publish time (full cycle)

```
Post published
  │
  ├─ Immediately (0–1 min):
  │   → /comment-own-post → first comment with the article link
  │
  ├─ 10–30 min:
  │   → /amplify → team comments (30% internal, 70% external)
  │   → Rule: team comments ≠ "Great post!" — they add their own experience/opinion
  │
  └─ First 30 min (continuous):
      → /comment-reply → reply to EVERY incoming comment
      → Timing rule: reply within the first 30 min = +64% comments (algorithm)
```

### Daily commenting routine

```
Every day (morning):
  → /comment-others [Author] → 3–5 comments on posts in your feed
  → Focus: posts from your target audience (ICP), thought leaders in the niche, potential customers
  → Rule: don't comment just for visibility — add real value
```

---

## 7. Core principles

### Content

| Principle | What it means |
|---------|---------------|
| **Repackaging, not writing** | The author's expertise is the foundation. We don't invent meaning or add our own takes |
| **Tone of Voice = DIP** | Each author speaks their own way. The DIP stores style, vocabulary, thought patterns |
| **Identity ≠ Repetition** | The DIP defines DEPTH and STYLE — not the same phrases in every post. "20 years in marketing" is fine once every 2 months, not in every post |
| **First person (I/my)** | ALWAYS in personal posts. "We/our" — only when really talking about the team |
| **One post = one file** | Edits overwrite. Do NOT create `-v2`, `-v3` |
| **Feedback Loop is mandatory** | After every piece of feedback → record it in the DIP. Before a new post → reread the Feedback Log |
| **Facts from source_refs** | Every statement is backed by a real quote from a transcript or document |

### Technical

| Principle | What it means |
|---------|---------------|
| **Validation agents = context: fork** | Each validator runs in an isolated subagent, doesn't pollute the main context |
| **Master validator orchestrates** | `/validate-post` runs all 3 checks + its own checklist. No need to run the checks separately |
| **Re-validate after edits** | Any change to a post → run `/validate-post` again. It's cheap and fast |
| **Don't touch the reference layer** | Files in `Content/LinkedIn/Skills/` are knowledge. SKILL.md files in `.claude/skills/` reference them, never duplicate |

---

## 8. Common mistakes (from validation practice)

These errors have already been caught by validation agents:

| Mistake | Example | How it's caught |
|--------|--------|-------------|
| **Compilation across contexts** | Client A case + Client B numbers → looks like one case | `/check-facts` |
| **Manual process → "AI agent did it"** | A person manually tested a hypothesis, but the post makes it sound like automation | `/check-facts` |
| **Repeated identity markers** | "20 years in marketing" in 3 posts within a month | `/check-generic` |
| **Repeated hook formula** | "Everyone thinks X. They're wrong." was already used 2 weeks ago | `/check-generic` |
| **Bro-etry** | One-line dramatic phrases for effect | `/check-generic` |
| **Statement without a source** | "Analysis that took 1.5h — 10 minutes" — where's the number from? | `/check-sources` |
| **Cluster monotony** | 5+ posts in a row in the same cluster (Performance Marketing) | `/validate-post` |

---

## 9. Key files (quick access)

### Meta-documents
- **This guide:** `Skills/00-LinkedIn-Skills-Guide.md`
- **Skills research:** `Skills/00-Skills-Research-Claude-Code.md`
- **LinkedIn Routing:** `Content/LinkedIn/CLAUDE.md`
- **Global Routing:** `.claude/CLAUDE.md`

### Reference Layer
- **Post Engine:** `Skills/04-Post-Creation-Engine/Post-Creation-Engine.md`
- **Comments Engine:** `Skills/06-Comments-Engine/Comments-Engine.md`
- **Algorithm:** `Skills/02-LinkedIn-Algorithm/Algorithm-Intelligence.md`
- **Trends:** `Skills/03-Viral-Trends/Current-Trends.md`
- **Hooks:** `Skills/03-Viral-Trends/Hook-Pattern-Library.md`
- **Anti-Patterns:** `Skills/03-Viral-Trends/Anti-Patterns.md`
- **Post Template:** `Skills/04-Post-Creation-Engine/Post-Template.md`

### Author DIPs
- **Seva:** `Skills/01-Digital-Identity-Profiles/Seva-Ustinov-DIP.md`
- **Kirill:** `Skills/01-Digital-Identity-Profiles/Kirill-Kasimskiy-DIP.md`

### SKILL.md files
- **Create Post:** `.claude/skills/create-post/SKILL.md`
- **Create Comment:** `.claude/skills/create-comment/SKILL.md`
- **Update DIP:** `.claude/skills/update-dip/SKILL.md`
- **Validate Post:** `.claude/skills/validate-post/SKILL.md`
- **Check Facts:** `.claude/skills/check-facts/SKILL.md`
- **Check Generic:** `.claude/skills/check-generic/SKILL.md`
- **Check Sources:** `.claude/skills/check-sources/SKILL.md`

---

## 10. Roadmap

### Done
- [x] Reference Layer: 7 documentation modules
- [x] Task Skills: `/create-post`, `/create-comment`, `/update-dip`
- [x] Validation Agents: `/check-facts`, `/check-generic`, `/check-sources`, `/validate-post`
- [x] Routing: CLAUDE.md + Content/LinkedIn/CLAUDE.md
- [x] 5 author DIPs

### In progress
- [ ] Testing `/validate-post` on real posts (first test: Seva funding announcement — completed 2026-02-26)
- [ ] Stabilizing DIPs for Denis (v0.7 → v1.0) and Ella (v0.5 → v1.0)

### Planned
- [ ] `/comment-own-post` — first comment on your own post
- [ ] `/comment-others` — comments on others' posts
- [ ] `/amplify` — cross-team amplification
- [ ] `/comment-reply` — replies to incoming comments
- [ ] LinkedIn API integration (auto-posting, engagement data collection)
- [ ] Automated Weekly Update for algorithm and trends
