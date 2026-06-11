---
name: create-dip
description: Creates a Digital Identity Profile (DIP) for a new author from scratch. Collects raw sources (transcripts, voice, Telegram), extracts Tone of Voice, Stories Bank, Expertise Clusters. ONLY from raw sources, NEVER from posts.
disable-model-invocation: true
argument-hint: [Author-Name]
allowed-tools: Read, Grep, Glob, Agent
---

# Create Digital Identity Profile (DIP)

Build a full DIP for a new author from scratch.

## Input

- `$0` — the new author's name (e.g., "Author Name")

## Required files

1. **DIP Template:**
   `Templates/DIP-Template.md`

2. **DIP Creation Workflow:**
   `Templates/DIP-Creation-Workflow.md`

3. **Transcript map:**
   From your repo's master CLAUDE.md → "Transcript map" section

## ⛔ CANONICAL SOURCE RULE

**The DIP is built ONLY from raw sources:**
- Transcripts of meetings, calls, webinars, podcasts
- The author's voice input
- Telegram posts personally written by the author
- CVs, articles, documents written by the author
- Transcripts of client interviews

**NEVER from:**
- LinkedIn posts (`Posted/`)
- PR comments
- Marketing copy
- Any AI-generated content

**Why:** DIP → Post → DIP = Feedback Loop. After 3–4 cycles the person's real voice is gone.

## Pipeline

### Phase 1: Source collection (30 min)

1. Identify the author's name
2. Look for transcripts across ALL locations on the transcript map:

| Type | Location |
|------|----------|
| Presales calls | `Sales/Presales/Projects/Projects list/*/Transcripts/` |
| Client meetings | `Production/Projects/Projects list/*/Meetings transcripts/` |
| AGI/Product calls | `your-transcripts/internal-product-calls/` |
| Granola (internal) | `your-transcripts/synced-meetings/` |
| Marketing calls | `your-transcripts/marketing-meetings/` |
| Podcasts/events | `your-raw-sources/podcasts-and-events/` |
| Webinars | `your-transcripts/webinars/` |
| Conferences | `Media activities/Cursor Case Activities/Conferences/` |
| Telegram | `your-raw-sources/telegram-posts/` |

3. Minimum 3 transcripts, ideally 5+. Variety of types matters more than quantity.
4. If sources are thin → tell the user, request more material.

### Phase 2: Tone of Voice extraction (60 min per transcript)

For each transcript, extract:

1. **Characteristic phrases** — how the person talks, their jargon
2. **Reasoning style** — how they build an argument
3. **Speech patterns** — start with an example? a thesis? a question?
4. **Emotional register** — serious? ironic? blunt? analytical?
5. **What they NEVER say** — "They NEVER" (forbidden patterns)

### Phase 3: Build the Stories Bank (60 min)

From the transcripts, extract:
- Concrete cases with detail (client, situation, outcome)
- Personal stories (career moments, failures, learnings)
- Metrics and numbers from real experience
- Quotes — verbatim phrases that characterize the person

For each story, record:
- Source (file, approximate line)
- Context (who said it, when, to whom)
- Key details

### Phase 4: Define Expertise Clusters (30 min)

Based on the transcripts, identify:
- 3–4 main expertise clusters
- Distribution across clusters (in %)
- Viral angles for each cluster

### Phase 5: Fill the template

Load `_DIP-Template.md` and fill every section:

1. **Identity & Position** — who, role, company
2. **Tone of Voice** — style, speech patterns, "They NEVER"
3. **Expertise Clusters** — 3–4 clusters with distribution
4. **Stories Bank** — 10+ stories with sources
5. **Viral Angles** — formulas for content
6. **Source Index** — list of all sources used
7. **Feedback Log** — empty (filled as posts are published)

### Phase 6: Save

Save to: `Knowledge-Base/01-Identity-Profiles/[Author-Name]-DIP.md`

Filename format: `FirstName-LastName-DIP.md` (hyphenated, title case)

### Phase 7: Register

Add the author to:
1. `Content/LinkedIn/CLAUDE.md` (or your project's master routing file) → author table
2. `.claude/CLAUDE.md` → author DIPs section
3. Your master skill guide (if it has an author table)

## Output

1. **Finished DIP file** — saved at the path above
2. **Summary** — brief recap: how many sources used, key author characteristics
3. **Source Index** — full list of files used
4. **Recommendations** — what else is needed for a full DIP (if sources are thin)

## Versioning

| Version | Minimum | Description |
|---------|---------|-------------|
| v0.5 | 1–2 sources | Bootstrap — basic tone, minimal stories |
| v0.7 | 3–4 sources | Working DIP — enough for posts, needs enrichment |
| v1.0 | 5+ sources, diverse types | Full DIP — ready for production |
