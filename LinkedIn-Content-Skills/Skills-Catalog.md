# Skills Catalog — Complete catalog of skills and their call chains

> How skills are wired technically, which chains they trigger, what each skill does step by step.

---

## Table of Contents

1. [What a skill is technically](#what-a-skill-is-technically)
2. [Map of all skills (24 total)](#map-of-all-skills)
3. [Call chains (which skill triggers which)](#call-chains)
4. [LinkedIn: Content creation (11 skills)](#linkedin-content-creation)
5. [LinkedIn: Validation (5 skills)](#linkedin-validation)
6. [Events: Webinars and events (7 skills)](#events-webinars-and-events)
7. [PR: Expert commentary (1 skill)](#pr-expert-commentary)
8. [How a skill is built internally (anatomy of SKILL.md)](#anatomy-of-skillmd)

---

## What a skill is technically

A skill is a `.claude/skills/[name]/SKILL.md` file. It contains:
- **Frontmatter (YAML)** — metadata: name, description, which tools are available
- **Pipeline** — step-by-step instructions for Claude Code

When a user types `/create-post Seva AI agents`, Claude Code:
1. Locates `.claude/skills/create-post/SKILL.md`
2. Reads the pipeline
3. Executes the steps in order
4. Loads reference files (DIP, algorithm, trends)
5. Generates the result
6. Automatically runs validation (if specified)

### Three types of skills

| Type | `disable-model-invocation` | `context` | What it does |
|------|---------------------------|-----------|--------------|
| **Worker** | `true` | — | Performs the work (writes a post, creates a DIP) |
| **Orchestrator** | `true` | — | Coordinates a chain of skills (validate-content) |
| **Validator** | `true` | `fork` | Checks the result in isolation (check-facts, detect-ai) |

**`context: fork`** = the skill runs in a separate context. Its work doesn't clutter the main conversation. Ideal for validators — they can load huge transcripts, compare, count — and return only a clean report.

---

## Map of all skills

### LinkedIn: Content creation (11)

| # | Skill | Command | What it does |
|---|-------|---------|--------------|
| 1 | `create-post` | `/create-post [Author] [topic]` | Creates a post via a 9-step pipeline |
| 2 | `create-dip` | `/create-dip [Author-Name]` | Creates a DIP for a new author from scratch using transcripts |
| 3 | `update-dip` | `/update-dip [Author]` | Updates a DIP with new data |
| 4 | `comment-on-post` | `/comment-on-post [Author]` | Comment from the author on SOMEONE ELSE'S post |
| 5 | `reply-to-comments` | `/reply-to-comments [Author]` | Batch replies to comments under the author's OWN post |
| 6 | `find-comment-targets` | `/find-comment-targets [Author]` | Finds posts to comment on |
| 7 | `suggest-next-post` | `/suggest-next-post [Author]` | Recommends the topic of the next post |
| 8 | `post-publication` | `/post-publication [Author]` | Golden window: the first 90 minutes after publishing |
| 9 | `optimize-profile` | `/optimize-profile [Author]` | LinkedIn profile optimization |
| 10 | `scan-telegram` | `/scan-telegram [Author]` | Scans Telegram to find content |
| 11 | `weekly-update` | `/weekly-update` | Weekly update of the whole system |

### LinkedIn: Validation (5)

| # | Skill | Command | What it does |
|---|-------|---------|--------------|
| 12 | `validate-content` | `/validate-content [file]` | **Orchestrator**: runs a chain of 5 checks |
| 13 | `check-facts` | `/check-facts [file]` | Factual accuracy, logic of compilations |
| 14 | `check-generic` | `/check-generic [file]` | Generic language, AI phrases, repetition vs the last 10 posts |
| 15 | `check-sources` | `/check-sources [file]` | Map: every claim → a specific source |
| 16 | `detect-ai` | `/detect-ai [file]` | 6-level AI detector + specific edits |

### Events: Webinars and events (7)

| # | Skill | Command | What it does |
|---|-------|---------|--------------|
| 17 | `create-event-concept` | `/create-event-concept [topic]` | Event concept via a 7-step pipeline |
| 18 | `create-speaker-brief` | `/create-speaker-brief [Speaker] [Event-slug]` | Deep speaker research + brief with questions |
| 19 | `create-event-promo` | `/create-event-promo [Event-slug]` | Promo package: LinkedIn posts, email, sharing kit |
| 20 | `plan-event-content` | `/plan-event-content [Event-slug]` | Content plan: 15+ units from the event |
| 21 | `validate-event-concept` | `/validate-event-concept [path]` | ICP fit, specificity, anti-patterns |
| 22 | `validate-speaker-brief` | `/validate-speaker-brief [path]` | Quality of research and questions |
| 23 | `validate-speaker` | `/validate-speaker [path]` | Speaker fit with the topic, audience, panel |

### PR (1)

| # | Skill | Command | What it does |
|---|-------|---------|--------------|
| 24 | `create-pr-commentary` | `/create-pr-commentary [Author] [outlet/topic]` | Expert commentary for a journalist |

---

## Call chains

### Chain 1: Creating a post (the longest one)

```
/create-post [Author] [topic]
│
├── Step 0: Fresh Scan → checks the DIP, if stale → updates it internally
├── Steps 1-7: post creation
│
└── Step 8: /validate-content [post file]    ← AUTOMATICALLY
              │
              ├── /check-facts          (fork) ← fact check
              ├── /check-generic        (fork) ← generic + repetition (pass 1)
              ├── /check-sources        (fork) ← source map
              ├── /detect-ai            (fork) ← 6-level AI detector
              └── /check-generic --second-pass (fork) ← after AI edits (pass 2)
```

**Total: 1 main skill triggers 1 orchestrator, which triggers 5 validators = 7 skills in the chain.**

### Chain 2: Creating an event concept

```
/create-event-concept [topic]
│
├── Steps 1-7: concept creation
│
└── /validate-event-concept [file]    ← AUTOMATICALLY
     └── 8 checks (ICP, specificity, speakers, KPI...)
```

### Chain 3: Speaker preparation

```
/create-speaker-brief [Speaker] [Event-slug]
│
├── Steps 1-7: deep research + brief
│
├── /validate-speaker-brief [file]    ← AUTOMATICALLY
│    └── 6 checks (research quality, questions, sources...)
│
└── /validate-speaker [file]          ← AUTOMATICALLY
     └── 5 checks (freshness, topic fit, panel fit, ICP...)
```

### Chain 4: PR commentary

```
/create-pr-commentary [Author] [outlet/topic]
│
├── Step 0: Fresh Scan DIP
├── Steps 1-7: commentary creation
│
└── /detect-ai [file]    ← AUTOMATICALLY
     └── 6-level AI detection
```

### Chain 5: Event promo

```
/create-event-promo [Event-slug]
│
├── Step 1: LinkedIn posts → uses Seva's DIP + Algorithm-Intelligence
│    └── each post = a mini /create-post (without calling the skill)
├── Step 2: Email
├── Step 3: Speaker Sharing Kit
├── Step 4: Paid Ads
└── Step 5: Coordination
```

### Chain 6: Weekly Update (coordinates all maintenance)

```
/weekly-update
│
├── Step 1: Performance Review (all authors)
├── Step 2: Content Audit (clusters, formats, gaps)
├── Step 3: Algorithm & Trends Scan → updates reference files
├── Step 4: Topic Backlog Review
│    └── if empty → recommends /suggest-next-post
├── Step 5: DIP Health Check
│    └── if stale → recommends /update-dip
└── Step 6: Weekly Report
```

### Chain 7: Post-Publication (coordinates engagement)

```
/post-publication [Author]
│
├── T+0-5: First comment (prepared during create-post)
├── T+5-15: Cross-team comments
├── T+15-30: Engagement routine
│    └── recommends /find-comment-targets → /comment-on-post
├── T+30-60: Reply to comments
│    └── recommends /reply-to-comments
└── T+60-90: Second round
```

---

## LinkedIn: Content creation

### `/create-post` — 9-step pipeline

**Call:** `/create-post Seva "AI agents replacing manual rules"`

**What gets loaded:**
1. The author's DIP (`Skills/01-Digital-Identity-Profiles/[Author]-DIP.md`) — **mandatory**
2. Post-Creation-Engine (`Skills/04-Post-Creation-Engine/Post-Creation-Engine.md`) — **mandatory**
3. Algorithm-Intelligence (`Skills/02-LinkedIn-Algorithm/Algorithm-Intelligence.md`) — **mandatory**
4. Current-Trends (`Skills/03-Viral-Trends/Current-Trends.md`) — recommended
5. Hook-Pattern-Library (`Skills/03-Viral-Trends/Hook-Pattern-Library.md`) — when choosing a hook
6. Benchmark-Validation-System (`Skills/04-Post-Creation-Engine/Benchmark-Validation-System.md`) — if there are numbers

**Pipeline:**

| Step | What happens | Details |
|------|--------------|---------|
| 0 | **Fresh Scan** | Checks the `Last Fresh Scan` date in the DIP. If new transcripts appeared → updates the DIP before starting work |
| 1 | **Load the DIP** | Tone of Voice, Expertise Clusters, Stories Bank, Viral Angles, Format Preferences |
| 2 | **Extract the core message** | One key thought. If there are several → suggests a series. Classification by cluster and pillar |
| 3 | **Pick the angle and format** | Angle from DIP Viral Angles + Current-Trends. Format from Algorithm-Intelligence. Check: doesn't repeat the format of the last 3 posts |
| 4 | **Writing** | Hook: first 140 characters (Hook-Pattern-Library). Body: short paragraphs, examples from the Stories Bank, numbers. CTA: specific. Length: 1200-1800 characters |
| 5 | **Internal validation** | Checklist: length, first person, no links in the first 300 characters, topic alignment, cluster rotation |
| 6 | **Output formatting** | Post text + 2-3 alternative hooks + format recommendation + publishing time |
| 7 | **Save** | `Posted/[Author]/YYYY-MM-DD-[slug].md` with metadata (source_refs, cluster, hook_type) |
| 8 | **Auto-validation** | Runs `/validate-content [file]` → chain of 5 checks |
| 9 | **After feedback** | Updates the DIP "FEEDBACK LOG & LEARNINGS" section |

**Key rules:**
- One post = one file. When reworking — overwrite, do NOT create -v2
- First person (I/my). NEVER we/our in personal posts
- All statements come from real sources (source_refs)
- Check overlap with posts from the past week

---

### `/create-dip` — creating a profile from scratch

**Call:** `/create-dip Author-Name`

**What gets loaded:**
1. DIP Template (`Skills/01-Digital-Identity-Profiles/_DIP-Template.md`)
2. DIP Creation Workflow (`Skills/01-Digital-Identity-Profiles/_DIP-Creation-Workflow.md`)
3. Transcript map from CLAUDE.md

**Pipeline (7 phases):**

| Phase | Time | What happens |
|-------|------|--------------|
| 1. Source Collection | 30 min | Search across ALL transcript locations (11 places). Minimum 3 transcripts, ideally 5+. Diversity of types matters more than quantity |
| 2. Tone of Voice | 60 min/transcript | Extracting characteristic phrases, reasoning patterns, emotional tone, "They NEVER" list |
| 3. Stories Bank | 60 min | Specific cases (client, situation, result), personal stories, metrics. For each one — a source file and approximate line |
| 4. Expertise Clusters | 30 min | 3-4 clusters with percentages. Viral angles for each |
| 5. Fill Template | — | Filling in all 9 sections of the DIP |
| 6. Save | — | `Skills/01-Digital-Identity-Profiles/[Author-Name]-DIP.md` |
| 7. Register | — | Add to the authors table in CLAUDE.md + Content/LinkedIn/CLAUDE.md |

**Versioning:**

| Version | Minimum sources | Status |
|---------|-----------------|--------|
| v0.5 | 1-2 | Bootstrap — basic tone, few stories |
| v0.7 | 3-4 | Working — enough for posts, needs enrichment |
| v1.0 | 5+ different types | Production — complete DIP |

**Canonical Source Rule:**
- **INPUT:** transcripts, voice input, personal Telegram posts, the author's CV/articles
- **NEVER INPUT:** LinkedIn posts, PR commentaries, marketing copy, AI-generated content
- **Why:** DIP → Post → DIP = a feedback loop, voice degrades over 3-4 cycles

---

### `/update-dip` — updating the profile

**Call:** `/update-dip Kirill`

**4 update types:**

| Type | When | What it does |
|------|------|--------------|
| New Transcript | A new transcript appeared | Extracts: new stories, patterns, frameworks, positions, metrics. Checks contradictions against the current DIP. Updates the Source Index |
| Feedback | The author gave feedback | Logs to the FEEDBACK LOG. If a pattern repeats 3+ times → moves it from the Feedback Log into the main DIP sections |
| Fresh Scan | Before content creation | Quick scan (5 min/file) of all new transcripts since Last Fresh Scan. If material updates → updates the DIP |
| Quarterly Review | Once a quarter | Check all sections for currency. Find unanalyzed transcripts. Update metrics (team size, clients, numbers) |

**Source priority (11 levels):**
1. Podcasts and talks → 2. Conferences → 3. Livestreams → 4. AGI/Product calls → 5. Presales → 6. Marketing → 7. AI positioning → 8. Client calls → 9. Granola syncs → 10. Webinars → 11. Telegram

---

### `/comment-on-post` — comment on someone else's post

**Call:** `/comment-on-post Seva`

**Pipeline (6 steps):**

| Step | What it does |
|------|--------------|
| 1 | Load DIP: Tone + Speech Patterns + "They NEVER" + Expertise Clusters + Stories Bank |
| 2 | Analyze the original post: topic, which cluster of the author it relates to, whether there's a unique perspective |
| 3 | Pick the formula: Share own experience / Clarify+add / Ask smart question / Contrarian position |
| 4 | Writing: min 15 words (2.5x weight in the algorithm), optimal 30-80 words, first person, specifics from the DIP Stories Bank |
| 5 | **Source Grounding** — check EVERY statement: Verified fact / Grounded inference / Thin ground / Bullshit. If >50% = thin/bullshit → rewrite |
| 6 | Validation: sounds like the author? adds value? doesn't sell? doesn't restate the post? |

**Forbidden patterns:**
- "Great post!" / "Love this!" / "So true!"
- Quoting a line from the post + "this is the key"
- Restating the metrics back at the author
- "I've seen..." without specifics
- Self-promotion on someone else's post

---

### `/reply-to-comments` — replying to comments

**Call:** `/reply-to-comments Seva`

**Why critical:** Reply within the first 30 minutes → +64% comments, 2.3x views

**Classification + formulas:**

| Comment type | Reply formula |
|--------------|---------------|
| Agreement / support | Expand + Add layer: "And what most miss is [deeper insight]" |
| Question | Answer + Bridge: "Short answer: [X]. Real answer: [nuance]" |
| Disagreement | Acknowledge + Reframe: "I see your point, but [counter-evidence]" |
| Compliment | Redirect to insight: "Real credit goes to [specific detail]" |
| "How do I learn more?" | Give value + soft CTA: "Here's where I'd start: [tip]" |
| Congratulations | Micro-response bank (rotate!) |

**Key rule: ROTATION.** No two identical replies in a row. If 10+ congratulations: 3-4 = emojis, the rest = words, and all different.

---

### `/find-comment-targets` — finding posts to comment on

**Call:** `/find-comment-targets Seva --strategy all`

**3 strategies:**

| Strategy | % | Who we look for |
|----------|---|-----------------|
| Topic | 40% | Posts on topics from the DIP Expertise Clusters |
| ICP | 30% | Posts from potential clients (Head of Growth, VP Marketing, CMO) |
| Networking | 30% | Thought leaders, podcast hosts, journalists in our niche |

**The skill does NOT go into LinkedIn.** It forms the strategy and search criteria. The user finds the posts, then calls `/comment-on-post`.

---

### `/suggest-next-post` — what to write next

**Call:** `/suggest-next-post Kirill`

**What it analyzes:**

| What | How |
|------|-----|
| Cluster balance | Last 10-15 posts: actual % vs target from the DIP |
| Format rotation | Last 5 posts: no 3+ of one format in a row |
| Timing | Days since the last post (>3 = urgent) |
| Topic Backlog | Inbox → scoring: cluster fit (30%) + trend match (25%) + unique angle (20%) + source readiness (15%) + urgency (10%) |

If the Topic Backlog is empty → suggests: DIP uncovered angles / Current Trends / `/scan-telegram` / fresh transcripts.

---

### `/post-publication` — golden window

**Call:** `/post-publication Seva`

**Timeline:**

| Time | Action |
|------|--------|
| T+0 | Post published |
| T+0-5 min | Author's first comment (prepared during create-post). 15+ words, doesn't restate the post |
| T+5-15 min | Cross-team: colleagues comment (each one — a unique angle) |
| T+15-30 min | Engagement routine: the author comments on 5-10 posts in the niche (→ algorithm sees activity → more reach) |
| T+30-60 min | Reply to ALL comments (→ `/reply-to-comments`) |
| T+60-90 min | Second round: 3-5 comments + check for new ones |
| T+90+ | Monitor every 2-3 hours. DO NOT publish a new post for 12 hours |

---

### `/optimize-profile` — profile optimization

**Call:** `/optimize-profile Seva`

**Why it matters:** 360Brew cross-checks posts against the profile. Semantic mismatch → suppressed distribution.

**8 steps:** Audit → Headline (max 220 chars, the first 60 are visible in the feed) → About (5 paragraphs, hook in the first 2 lines) → Experience (with metrics) → Skills (5+ = 2.9x views) → Photo/Banner → Verifications → Validation

---

### `/scan-telegram` — Telegram scan

**Call:** `/scan-telegram Seva`

**Why Telegram is a valuable source:** posts are written PERSONALLY by the author (not AI), engagement shows what resonates, the style is closer to conversational.

**Pipeline:** Find posts → Engagement scoring (reactions × 3 + comments × 5 + reposts × 10) → Topic extraction (which DIP cluster?) → Repackaging suggestions (was it already on LinkedIn? does it fit current trends?) → Prioritized report

---

### `/weekly-update` — weekly update

**Call:** `/weekly-update`

**6 steps (~95 minutes):**

| Step | Time | What it does |
|------|------|--------------|
| 1. Performance Review | 30 min | Weekly metrics for each author. Best/worst post, trend |
| 2. Content Audit | 20 min | Number of posts, cluster balance, format rotation, gaps |
| 3. Algorithm & Trends Scan | 20 min | Update Algorithm-Intelligence and Current-Trends if needed |
| 4. Topic Backlog Review | 15 min | Published → Done. Anything in Prioritized? If empty → `/suggest-next-post` |
| 5. DIP Health Check | 10 min | Version, unrecorded feedback, 5+ posts since last update → recommend `/update-dip` |
| 6. Weekly Report | — | Summary table: performance, audit, trends, backlog, DIP health, action items |

---

## LinkedIn: Validation

### `/validate-content` — orchestrator

**Call:** `/validate-content path/to/post.md --type post`

**Auto-detection of type:** based on file contents (frontmatter, sections).

**5 phases (in sequence):**

| Phase | Skill | Context | What it checks |
|-------|-------|---------|----------------|
| 1 | `/check-facts` | fork | Factual accuracy, logic of compilations from multiple sources |
| 2 | `/check-generic` | fork | Generic phrases, AI language, repetition vs the last 10 posts (pass 1) |
| 3 | `/check-sources` | fork | Map: every claim → a specific transcript/source |
| 4 | `/detect-ai` | fork | 6 levels of AI detection + specific edits |
| 5 | `/check-generic --second-pass` | fork | Re-check after AI edits (pass 2) |

**Type-specific checks (between phase 3 and 4):**

For **post**: length 1200-1800, format rotation, cluster balance, hook < 140 chars, anti-patterns (engagement bait, bro-etry, we/our, links in the opening), mobile readability

For **comment**: min 15 words, first person, not generic, doesn't sell, source grounding

For **profile**: headline ≤120 chars, about with a hook, specifics, DIP tone

For **pr**: ≤150 words, quotable sentence, no marketing language, specifics

**Output:** summary table across all checks + prioritized recommendations (Critical → Important → Optional)

---

### `/check-facts` — fact check

**Context:** fork (isolated)

**Algorithm:**
1. Reads the post + all source_refs from the frontmatter
2. For EACH specific statement (numbers, events, names, results):
   - Locates it in the source (file, line, verbatim quote)
   - If from several sources → marks as a COMPILATION
3. Checks the logic of compilations (typical errors):
   - A manual experiment → sounds like automation
   - Numbers from different contexts in a single statement
   - Time compression (6-month results sound like current practice)
   - Attribution (someone else's words → attributed to another person)
   - A hypothesis vs a confirmed result
4. Without a source → flags it

---

### `/check-generic` — generic check

**Context:** fork

**Two modes:**
- **Pass 1 (default):** full check — generic phrases + repetition vs the last 10 posts + tonal alignment with the DIP
- **Pass 2 (`--second-pass`):** generic + tone only (after AI edits, skip repetition history)

**What it looks for:**

| Category | Examples |
|----------|----------|
| Empty intensifiers | "incredibly", "game-changing", "revolutionary", "transformative" |
| LinkedIn clichés | "In today's world...", "Let me share...", "Excited to announce..." |
| AI language | Overly smooth transitions, "Furthermore", "Moreover", uniform sentence length |
| Abstractions without specifics | Any sentence that would apply to ANY company/product |
| "They NEVER" from the DIP | Checks against the author's personal banned list |

**Identity ≠ Repetition:** The DIP defines JARGON, DEPTH, LINE OF THINKING. NOT repeating the same phrases in every post. "20+ years in performance marketing" in 3 posts in a row → problem.

---

### `/check-sources` — source map

**Context:** fork

**For EACH statement, it classifies as:**

| Type | Meaning |
|------|---------|
| Direct quote | Almost word-for-word from a single source (file, line, quote) |
| Compilation | Assembled from SEVERAL places (shows each fragment separately + context-match score) |
| Author opinion | Not found in source_refs (fine if not passed off as fact) |
| Common knowledge | A well-known fact, no source needed |

**Bonus:** checks the reverse — if a source_ref is listed in the frontmatter but nothing from it is used → flags it as excessive.

---

### `/detect-ai` — 6-level AI detector

**Context:** fork

**Main principle:** The hook (the first 1-3 lines) = UNTOUCHABLE (it follows virality rules). Everything else must sound human.

| Level | What it checks | Example problem | Example fix |
|-------|----------------|-----------------|-------------|
| **1. Lexicon** | AI words (40+ in EN dictionary + 10+ RU), filler openers, hedge phrases, transition fillers | "leverage our insights" | "use what we've learned" |
| **2. Sentence structure** | Uniform length (std dev < 4 words), formulaic paragraphs, parallel constructions, passive voice (>30%), copula avoidance | All sentences are 14-16 words | Split the 3rd into two short ones |
| **3. Formatting** | Em dash overuse (>1/5 sentences), bold overuse (>3/1000 chars), inline-header pattern, symmetrical lists, rule of three (>2 lists of 3 items) | All list items are ±3 words of the same length | Vary it: 5 words, then 20, then 8 |
| **4. Tonal markers** | Relentless positivity, both-sides cop-out, significance inflation, vague attribution, meta-commentary | "Both approaches have merits" | "Option A wins if speed. Option B if accuracy." |
| **5. Content markers** | Abstraction over specificity, treadmill effect (two sentences = one thought in different words), missing personal stakes | "This approach significantly improves efficiency" | What specifically, by how much, for whom |
| **6. Rhythm** | Burstiness (human = jagged: 4 words → 22 → 8; AI = flat: 15 → 16 → 14), paragraph length variation | Range between longest and shortest <10 words | Add one of 3-5 words + one of 20+ |

**AI Score:**

| Findings | Score | Verdict |
|----------|-------|---------|
| 0-2 | HUMAN | Sounds human |
| 3-5 | LOW AI | Minimal edits |
| 6-10 | MEDIUM AI | Noticeable AI patterns, work needed |
| 11-15 | HIGH AI | Clearly AI-generated, serious rewrite |
| 16+ | REWRITE | Easier to write from scratch |

---

## Events: Webinars and events

### `/create-event-concept` — event concept

**7 steps:** Core idea → Target Audience (ICP check) → Positioning + 3-5 takeaways → Goals + KPIs → Format + Agenda → Speaker Wishlist → Save + Validate

**Loads:** Event-Concept-Engine, Event-Concept-Template, ICP-Reference, existing concepts (to check overlap)

**Saves to:** `Content/Online Events/Plurio-Webinar-Series/[Event-Slug]-Concept.md`

### `/create-speaker-brief` — speaker preparation

**7 steps:** Load event context → Deep research (internal Grep + external WebSearch) → Unique angle → 10-15 questions (Tier 1/2/3, each grounded in real research) → Deliverable request → Distribution commitment → Validate × 2

**Rule:** NO question may be generic. Test: remove the speaker's name. Could you ask it of ANYONE? → generic → rewrite.

### `/create-event-promo` — promo package

**5 steps:** LinkedIn series (5-7 posts, T-14 to T+0) via Seva's DIP → Email (3 subject-line variants) → Sharing Kit for speakers → Paid Ads → Coordination

### `/plan-event-content` — content plan

**4 steps:** Pre-event content map → Post-event plan (15+ units: replay, transcription, quotes, clips, cards, blog, post series) → Distribution calendar → Cross-promotion with the series

### `/validate-event-concept` — 8 checks

ICP Fit → Specificity → State Before→After → Unique Angle → Speaker-Topic Fit → KPI Realism → Topic Overlap → Anti-Patterns

### `/validate-speaker-brief` — 6 checks

Research Quality → Question Quality → Unique Angle → Deliverable Request → Distribution Kit → Source Completeness

### `/validate-speaker` — 5 checks

**Difference from validate-speaker-brief:** brief checks the DOCUMENT (research quality), speaker checks the PERSON (fit with the event).

Freshness (>14 days = STALE) → Topic-Audience Fit (matrix: speaker's topic × audience pain) → Event Theme Fit → Speaker Panel Fit (diversity matrix + compatibility matrix) → ICP Alignment

---

## PR: Expert commentary

### `/create-pr-commentary` — commentary for a journalist

**Call:** `/create-pr-commentary Seva "TechCrunch AI marketing automation"`

**9 steps:** Fresh Scan DIP → Load PR-Commentary-Engine → Load DIP → Analyze the journalist's request → Source Mining (search across all transcripts) → Source Map → Write (HOOK + MEAT + TAKEAWAY) → Humanizer Pass → Format + Checklist → Auto `/detect-ai`

**Rules:**
- Substance, not filler. Every sentence = a fact, a number, or a unique position
- 3-5 pull quotes (standalone quotes for the journalist)
- No product pitch. Plurio = context, not advertising
- Better to skip a question than answer it generically

**Saves to:** `Media activities/PR/Commentary-opportunities/Comment-YYYY-MM-DD-[Topic-Slug]-[Author].md`

---

## Anatomy of SKILL.md

### Full file structure

```yaml
---
# === METADATA ===
name: create-post                    # name = directory = /slash-command
description: "Creates a LinkedIn post" # Claude Code uses this for routing
disable-model-invocation: true       # true = only via /command, not automatically

# === CONTEXT ===
context: fork                        # fork = isolated context (for validators)
agent: general-purpose               # agent type (for fork)

# === ARGUMENTS ===
argument-hint: "[Author] [topic]"    # hint to the user

# === TOOLS ===
allowed-tools: Read, Grep, Glob, Write, Edit, Bash(python *), Skill(validate-content *)
# Read           — read files
# Grep           — search inside file contents
# Glob           — find files by pattern
# Write          — create files
# Edit           — edit files
# Bash(python *) — ONLY python scripts, not arbitrary bash
# Skill(validate-content *) — ONLY specific skills
---
```

### File body

```markdown
# Skill name

## When to use
[Triggers]

## Required files to load
1. **[Name]** (required): `path/to/file.md`
2. **[Name]** (recommended): `path/to/file.md`

## Pipeline

### Step 1: [Name]
[Instructions — what to read, what to do, which rules to follow]

### Step 2: [Name]
[Instructions]

...

### Step N: Save
[Where to save, in what format]

## Checklist
- [ ] [check 1]
- [ ] [check 2]

## Output format
[Report/result template]

## Related skills
[Which skills to trigger afterwards]
```

### Tool restrictions (patterns)

| Pattern | Meaning |
|---------|---------|
| `Bash(python *)` | Python scripts only |
| `Skill(validate-content *)` | Only the validate-content skill |
| `Skill(check-facts *), Skill(check-generic *)` | Only specific validators |
| `WebSearch` | Internet search (for speaker research) |
| `Agent` | Subtask spawning (for parallel research) |

---

## Summary table: skill → tools → loaded files → called skills

| Skill | Tools | Reference Files | Calls |
|-------|-------|-----------------|-------|
| `create-post` | Read, Grep, Glob, Edit, Write, Bash(py) | DIP, Post-Engine, Algorithm, Trends, Hooks, Benchmarks | → validate-content |
| `create-dip` | Read, Grep, Glob, Agent | DIP-Template, Creation-Workflow | — |
| `update-dip` | Read, Grep, Glob, Edit | Current DIP, Update-Workflow | — |
| `validate-content` | Read, Grep, Glob, Skill | (from file) | → check-facts, check-generic, check-sources, detect-ai, check-generic #2 |
| `check-facts` | Read, Grep, Glob | (from file sources) | — |
| `check-generic` | Read, Grep, Glob | DIP, Posted last 10 | — |
| `check-sources` | Read, Grep, Glob | (from file sources) | — |
| `detect-ai` | Read, Grep, Glob | (from file) | — |
| `comment-on-post` | Read, Grep, Glob | DIP, Comments-Engine | — |
| `reply-to-comments` | Read, Grep, Glob | DIP, Comments-Engine | — |
| `find-comment-targets` | Read, Grep, Glob | DIP, Algorithm, ICP, Trends | — |
| `suggest-next-post` | Read, Grep, Glob | DIP, Topic-Backlog, Posted, Algorithm, Trends | — |
| `post-publication` | Read, Grep, Glob | DIP, Comments-Engine, Algorithm | — |
| `optimize-profile` | Read, Grep, Glob | DIP, Profile-Guide, Algorithm, Posted | — |
| `scan-telegram` | Read, Grep, Glob | DIP, Algorithm, Trends, TG source, Posted | — |
| `weekly-update` | Read, Grep, Glob, Agent | Algorithm, Trends, Perf-Log, Posted, Backlog | → suggest-next-post, update-dip |
| `create-event-concept` | Read, Grep, Glob, Write, WebSearch | Event-Engine, Template, ICP, Existing events | → validate-event-concept |
| `create-speaker-brief` | Read, Grep, Glob, Write, WebSearch | Speaker-Engine, Template, Event-Concept, ICP | → validate-speaker-brief, validate-speaker |
| `create-event-promo` | Read, Grep, Glob, Write | Promo-Engine, Concept, Briefs, Seva-DIP, Algorithm, Email | (via create-post) |
| `plan-event-content` | Read, Grep, Glob, Write | Content-Plan-Engine, Concept, Briefs, Cases, Seva-DIP | — |
| `validate-event-concept` | Read, Grep, Glob | Concept, ICP, Other concepts | — |
| `validate-speaker-brief` | Read, Grep, Glob | Brief, Concept | — |
| `validate-speaker` | Read, Grep, Glob, WebSearch | Brief, Concept, All briefs, ICP | — |
| `create-pr-commentary` | Read, Grep, Glob, Edit, Write, Bash(py) | PR-Engine, DIP, Example commentary | → detect-ai |
