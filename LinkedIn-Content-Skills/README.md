# LinkedIn Skills System — Team Playbook

> How the LinkedIn content creation system works via Claude Code Skills.
> What you can take for yourself and how to adapt it to your own project.

---

## Table of Contents

1. What it is and why
2. Architecture: 3 layers
3. How post creation works — the full cycle
4. Digital Identity Profile (DIP) — the author's voice
5. Platform algorithm — what the system knows
6. Validation — the check chain
7. Growth Plan + Growth Loop — systematic growth (see paired files `Growth-Plan-Template.md`, `Growth-Loop-Architecture.md`)
8. Before → After (typical pattern)
9. What you can take for yourself
10. How to set it up for your own project

---

## What it is and why

This is a system for automating LinkedIn content via Claude Code. Not "AI writes posts" — it's **repackaging the author's real expertise** into a format that works on the platform.

**The problem without a system:**
- The author knows a lot but doesn't write — no time
- Content turns out generic — "like everyone else"
- The author's voice fades after 2–3 iterations with AI
- No connection between the platform's algorithm and what gets published
- Validation = "looks fine, I guess"

**With the system:**
- Content is built from real transcripts (calls, podcasts, webinars)
- The author's voice is locked into a profile (DIP) and doesn't degrade
- The LinkedIn algorithm (360Brew) is factored in at every step
- 5-level automatic validation
- Works for any team size — from a single founder to 5+ authors in parallel

---

## Architecture: 3 layers

```
┌─────────────────────────────────────────────────┐
│  LAYER 3: VALIDATION (Quality Control)          │
│  /check-facts → /check-generic → /check-sources │
│  → /detect-ai → /check-generic #2               │
│  Each validator = isolated agent (fork)         │
└────────────────────┬────────────────────────────┘
                     │ invoked automatically
┌────────────────────┴────────────────────────────┐
│  LAYER 2: ACTION SKILLS (Task Skills)           │
│  /create-post, /comment-on-post, /update-dip... │
│  Invoked via /slash commands                    │
│  Orchestrate a multi-step pipeline              │
└────────────────────┬────────────────────────────┘
                     │ loads
┌────────────────────┴────────────────────────────┐
│  LAYER 1: KNOWLEDGE BASE (Reference Layer)      │
│  Author DIP profiles                            │
│  Platform algorithm (Algorithm-Intelligence)    │
│  Viral trends (Current-Trends)                  │
│  Hook patterns (Hook-Pattern-Library)           │
│  Formats and benchmarks                         │
└──────────────────────────────────────────────────┘
```

### How it works technically

**Layer 1 (Reference)** — markdown files with up-to-date data. They live in `Skills/01-...`, `Skills/02-...`, etc. Updated weekly.

**Layer 2 (Skills)** — files at `.claude/skills/[skill-name]/SKILL.md`. Each is a set of step-by-step pipeline instructions for Claude. Invoked via `/slash commands`.

**Layer 3 (Validation)** — separate validator skills that run in an isolated context (fork). They don't pollute the main conversation.

---

## How post creation works

Full cycle of `/create-post [Author] [topic]`:

### Step 0: Fresh Scan
Check whether new transcripts for the author have appeared since the last scan. If yes — run `/update-dip` first.

### Step 1: Load the author's DIP
Load the profile: tone, expertise clusters, story bank, viral angles, format preferences.

### Step 2: Extract the key message
From the raw material (transcript, voice input), pull out ONE main idea. Classify it by cluster and editorial pillar.

### Step 3: Pick angle and format
- Angle — from DIP Viral Angles + current trends
- Format — based on Algorithm-Intelligence (carousel, text, video)
- Check: doesn't the format repeat what was used in the last 3 posts?

### Step 4: Write the post
- **Hook:** the first 140 characters (before "See more") — must stop the scroll
- **Body:** short paragraphs, concrete examples, numbers
- **CTA:** specific, not "agree?"

### Step 5: Internal validation
Checklist: length 1200–1800 characters, first person, no links in the first 300 characters, topic alignment with the author's headline, rotation of clusters and formats.

### Step 6: Format the output
Post text + 2–3 alternative hooks + format recommendation + publish time.

### Step 7: Save
`Posted/[Author]/YYYY-MM-DD-[slug].md` with full metadata (source_refs, cluster, hook type, status).

### Step 8: Automatic validation
`/validate-content` runs → a chain of 5 checks (see "Validation" below).

---

## Digital Identity Profile

**DIP is the "digital fingerprint" of an author's voice.** Not a description of the person, but instructions for the AI: how this person sounds, what they talk about, which phrases they use, which words they avoid.

### DIP structure (9 sections)

| # | Section | Contents | Example |
|---|---------|----------|---------|
| 1 | **Identity** | Role, background, positioning | "Founder who runs entire company on AI" |
| 2 | **Tone of Voice** | 6+ traits with verbatim examples, speech patterns, language rules (DO/NEVER) | "Direct, no fluff. Hook-first." |
| 3 | **Expertise Clusters** | Topic distribution (30/30/20/20%), subtopics, post ideas | AI-Teams 30%, Perf Marketing 30% |
| 4 | **Frameworks & Principles** | Named frameworks, recurring principles | "Vibe marketing: strategy stays human" |
| 5 | **Stories Bank** | Concrete stories with context markers | "Built 150-person agency... almost broke me" |
| 6 | **Viral Angles** | Proven angles that resonate | Contrarian takes, founder journey, case studies |
| 7 | **Format Preferences** | Which visual formats work for the author | Carousels for playbooks |
| 8 | **Feedback Log** | What worked / didn't work after publishing | "Data shock hooks → 2x engagement" |
| 9 | **Metadata** | Version, update date, sources | v1.2, 10+ transcripts |

### Canonical Source Rule (CRITICAL)

```
RAW SOURCES (INPUT)                  FINISHED CONTENT (OUTPUT)
─────────────────────                 ──────────────────────
✅ Call transcripts                   ❌ LinkedIn posts
✅ Podcasts and interviews            ❌ PR comments
✅ Author's voice input               ❌ Marketing copy
✅ Telegram (personally written)      ❌ Presentations
✅ CV, author's articles              ❌ AI-generated text

         │                                     │
         ▼                                     ▼
   Go into the DIP                     NEVER go into the DIP
```

**Why:** If you feed the DIP with your own posts, the voice degrades within 3–4 cycles. Posts are output. Transcripts are input. One-way flow only.

---

## Platform algorithm

The system collects and updates knowledge about how LinkedIn (360Brew) ranks content.

### What the system knows (updated weekly)

**8 ranking factors (March 2026):**

| # | Factor | Weight | What we do |
|---|--------|--------|------------|
| 1 | Profile-Content Alignment | Critical | Author's headline = post topics |
| 2 | Topic Consistency | Critical | 90 days across 3–4 clusters = authority |
| 3 | First Sentence Anchor | Critical | The first line gets disproportionate weight |
| 4 | Saves > Likes | Very high | 1 save = 5–10 likes. Build save-worthy content |
| 5 | Comments Train Profile | High | What you comment on = what you get shown |
| 6 | Links = Penalty | High | –60% reach. If a link is needed — after 300 characters |
| 7 | Structure Aids AI | Medium | Short paragraphs, lists → AI parses better |
| 8 | Hashtags = Minimal | Low | 1–3 max. 360Brew understands context without them |

**Engagement hierarchy (by weight):**
1. Saves (5–10x like)
2. DM shares
3. Reposts from influential users
4. Comments 15+ words (2.5x)
5. Thread depth
6. Dwell time 31–60 sec
7. Regular comments (2x likes)
8. Click "See more"
9. Likes (baseline)

**Dead signals (suppressed):**
- "Great post!" comments
- Engagement pods (60–90 day shadow ban)
- Engagement bait ("Agree?")
- Hashtag stuffing (5+)
- 2+ posts per day (–40% reach on each)

### Viral trends

What's working right now:
- Practical frameworks as carousels (6–9 slides)
- Build-in-public with real numbers
- Deep text posts (360Brew rewards depth)
- AI tools + real results
- Contrarian takes with evidence

What's dying:
- Generic "5 agents every founder needs" listicles
- Prompt-sharing posts
- Polls (–35% reach)
- "Link in first comment" (penalized 2026)
- Bro-etry

---

## Validation

Every post goes through an automatic chain of 5 checks:

```
/validate-content
  ├── /check-facts      — factual accuracy, logic
  ├── /check-generic    — generic phrases, AI-speak, repetition vs last 10 posts
  ├── /check-sources    — every claim → a specific source
  ├── /detect-ai        — 6-level AI detector (vocabulary → structure → tone → rhythm)
  └── /check-generic #2 — second pass after edits
```

### /detect-ai: 6 levels of analysis

| Level | What it checks | Example issue |
|-------|----------------|---------------|
| 1. Vocabulary | AI words and phrases | "leverage", "ecosystem", "in today's landscape" |
| 2. Sentence Structure | Uniform sentence length | All sentences 15–20 words |
| 3. Formatting | Over-structuring | Lists where a human wouldn't use them |
| 4. Tone | Unnatural evenness | No emotional peaks or valleys |
| 5. Content | Generic claims with no specifics | "AI is transforming the industry" |
| 6. Rhythm | Predictable prose rhythm | No short, clipped sentences |

Each validator runs in an isolated context (fork) — it doesn't affect the main conversation.

---

## Before → After (typical pattern)

### Transformation template

**BEFORE (raw input):**

- Raw transcript of a webinar / podcast / call — conversational, wordy, in the author's native language
- Key numbers and stories are buried in a 15-minute narrative
- The style doesn't fit the platform format (long, associative, no hooks)

**AFTER (LinkedIn post):**

- Data-shock hook in the first line (a concrete number + a concrete question to the reader)
- 3–5 paragraphs with specific steps / takeaways
- Author's voice preserved (verbatim phrases from their DIP)
- Specific CTA (not "agree?", but a question that requires a personal opinion)
- Length 1200–1800 characters, format — text / carousel depending on the topic

### What the system does at every transformation

1. **Extract numeric anchors** — finds concrete numbers, metrics, and timeframes in the source
2. **Hook compression** — turns a 30-second setup into a 140-character first line
3. **Voice preservation** — keeps the author's signature phrases from the DIP instead of smoothing them into an averaged AI style
4. **Format selection** — picks text / carousel / video based on content type (framework → carousel, story → text)
5. **CTA targeting** — phrases the CTA so it drives the specific metric that's currently underperforming (see Growth Loop)

> **Full worked examples** with real posts aren't included in this pack — they're tied to specific authors. Once you've collected 5–10 of your own transformations, add them to `Posted/[Author]/_Examples/` as references for future posts.

---

## What you can take for yourself

### 🟢 Take immediately (universal)

**1. The DIP concept (Digital Identity Profile)**
Build a voice profile for every author. Even without the rest of the system, a DIP dramatically improves AI-generated content. Minimal DIP:
- Tone of Voice (5–6 traits + examples)
- Expertise Clusters (3–4 topics with percentages)
- Stories Bank (5–10 stories)
- Language Rules (DO / NEVER)

**2. Canonical Source Rule**
INPUT → DIP → OUTPUT. Never feed AI its own output. This is the single rule that prevents voice degradation.

**3. The validation chain**
Even without the skills, check content against the sequence: facts → generic language → sources → AI detection. You can do this manually with prompts.

**4. Algorithm Intelligence**
Collect and maintain knowledge about how your platform works. Not LinkedIn? Same principle for X, Telegram, YouTube. Format: ranking factors + engagement hierarchy + dead signals.

**5. Hook Pattern Library**
A library of proven hook formulas. Works on any platform.

### 🟡 Adapt (needs configuration)

**6. Post Creation Pipeline**
The 8 steps can be adapted to any content. Steps 1–3 (load profile, extract message, pick angle) are universal. Steps 4–5 (writing, validation) are tied to the platform.

**7. Format Catalog**
Build your own format catalog with performance data for your platform.

**8. Comments Engine**
The comment system (15+ words, timing, response formulas) is adaptable to any social network.

### 🔴 Specific (doesn't transfer directly)

- Source Map (transcript map) — you'll have your own sources
- Specific DIP profiles — those are our authors
- ICP-specific framing — your ICP is different

---

## How to set it up for your own project

### Step 1: Build the Reference Layer (1–2 days)

```
your-project/
├── Skills/
│   ├── 01-Identity-Profiles/     ← DIPs of your authors
│   │   ├── _DIP-Template.md      ← template (see below)
│   │   └── Author-Name-DIP.md
│   ├── 02-Platform-Algorithm/    ← YOUR platform's algorithm
│   │   └── Algorithm-Intelligence.md
│   ├── 03-Trends/                ← what's working right now
│   │   ├── Current-Trends.md
│   │   └── Hook-Pattern-Library.md
│   └── 04-Creation-Engine/       ← creation pipeline
│       ├── Creation-Engine.md
│       └── Post-Template.md
├── Posted/
│   └── [Author]/                 ← published content
└── CLAUDE.md                     ← routing for Claude Code
```

### Step 2: Build a minimal DIP (2–3 hours per author)

Template:

```markdown
# [Author Name] — Digital Identity Profile

## 1. IDENTITY
- Role:
- Background (2–3 sentences):
- Positioning (1 phrase):

## 2. TONE OF VOICE
| Trait | Example (verbatim) |
|-------|--------------------|
| [e.g. Direct] | "[quote from transcript]" |
| [e.g. Data-driven] | "[quote]" |

### Speech patterns
- Signature phrase:
- Framing:
- Grounding:

### Language Rules
✅ DO: [specific rules]
❌ NEVER: [what's forbidden]

## 3. EXPERTISE CLUSTERS
| Cluster | % | Subtopics |
|---------|---|-----------|
| [Topic A] | 30% | ... |
| [Topic B] | 30% | ... |

## 4. STORIES BANK
| # | Story | Context | Use when |
|---|-------|---------|----------|
| 1 | ... | ... | ... |

## 5. FEEDBACK LOG
| Date | Post | What worked | What didn't |
|------|------|-------------|-------------|
```

### Step 3: Collect Algorithm Intelligence (4–6 hours)

For your platform, answer the following:
1. What are the ranking factors? (top 8)
2. Which engagement type carries the most weight?
3. What gets suppressed/penalized?
4. What's the content lifecycle?
5. Optimal length/format?

### Step 4: Write CLAUDE.md with routing

```markdown
# CLAUDE.md

## Routing
| Request | What to load |
|---------|--------------|
| "Create a post for [Author]" | DIP + Engine + Algorithm |
| "Check this post" | Validation chain |
| "What should I write about?" | Trends + DIP backlog |
```

### Step 5: (Optional) Build Claude Code Skills

Each skill = a file at `.claude/skills/[name]/SKILL.md`:

```yaml
---
name: create-post
description: Creates a post for an author following the pipeline
allowed-tools: Read, Grep, Glob, Write, Edit
---

## Pipeline

### Step 1: Load the author's DIP
Read file: `Skills/01-Identity-Profiles/[Author]-DIP.md`

### Step 2: ...
```

---

## Files in this pack

### Documentation (how it works)

| File | Contents |
|------|----------|
| `README.md` | This document — system overview, architecture, FAQ |
| `Skills-Catalog.md` | Full skills catalog: each pipeline, call chains, loaded files, output format |
| `LinkedIn-Knowledge-Base.md` | Large aggregated document: algorithm, formats, hooks, anti-patterns in one place |
| `Algorithm-Research-System.md` | How the algorithm knowledge system works: sources, updates, usage |
| `LinkedIn-Algorithm-Playbook-2026.md` | Deep dive into the 360Brew algorithm (LinkedIn 2026) |
| `00-LinkedIn-Master-Skill.md` | Master routing across skills (quick navigation) |
| `00-LinkedIn-Skills-Guide.md` | Guide to the skills with examples |
| `00-Skills-Research-Claude-Code.md` | How to build/extend skills for Claude Code |
| `Connection-Notes-Best-Practices.md` | Connection strategy: what to write in connection requests |
| `First-Touch-Best-Practices.md` | Best practices for first contact |

### Systematic growth (paired)

| File | Contents |
|------|----------|
| `Growth-Plan-Template.md` | Growth Plan template: causal model, formulas, phased strategy, KPIs |
| `Growth-Loop-Architecture.md` | Closed-loop architecture: targets → create → collect → analyze → adjust |
| `LinkedIn-Learning-Synthesis-Prompt.md` | Meta-prompt: how to turn an external course library into a Plan/Loop without copying copyrighted material |

### Articles + GEO (long-form pillar content)

| What | Where |
|------|-------|
| `Articles/README.md` | Section overview + how to use the examples |
| `Articles/Articles-Plan-Template.md` | Plan template for an Articles series optimized for AI-search |
| `Articles/_Examples/` | 5 worked examples — Articles actually published by the Plurio team |
| `Knowledge-Base/10-Articles-and-GEO/LinkedIn-Articles-GEO-Framework.md` | GEO + LinkedIn methodology for long-form |
| `Knowledge-Base/10-Articles-and-GEO/LLM-Visibility-Audit-Methodology.md` | How to check whether ChatGPT/Perplexity/Google AI actually cite your content |
| `Hook-Bank.md` | Hook library with persona × awareness × formula mapping (Plurio version, adaptable) |

### Knowledge Base (`Knowledge-Base/`)

All live reference documents. Structure:

```text
Knowledge-Base/
├── 02-LinkedIn-Algorithm/      # Algorithm + AI-detection + format data + posting times
├── 03-Viral-Trends/            # Hook library + current trends + anti-patterns + watchlist
├── 04-Post-Creation-Engine/    # Creation pipeline: engine + voice + template + benchmarks + refs
├── 05-Format-Testing/          # Format catalog + performance log + experiments
├── 06-Comments-Engine/         # Commenting as the author
├── 07-Auto-Update/             # Weekly update workflow
├── 08-Profile-Optimization/    # Headline / About / Skills / Verifications
├── 09-Visual-Design/           # Visual system + Lovable carousel instructions
└── 10-Articles-and-GEO/        # Long-form pillar content + AI-search optimization
```

### Templates (`Templates/`)

| File | Contents |
|------|----------|
| `DIP-Template.md` | Digital Identity Profile template (full version) |
| `DIP-Creation-Workflow.md` | How to build a DIP from scratch using raw sources |
| `DIP-Update-Workflow.md` | How to update a DIP without creating a feedback loop |
| `DIP-Template-Portable.md` | Lightweight DIP template you can port into your own project |
| `Voice-Vocabulary-Template.md` | Voice Vocabulary template: 9-section dictionary of an author's signature phrases for humanization |
| `Algorithm-Template.md` | Template for collecting platform algorithm data |
| `Skill-Template.md` | Claude Code Skill template with an example |
| `Validation-Prompts.md` | 5 ready-made prompts for manual validation (work in any AI) |

### Claude Code Skills (`.claude/skills/`)

19 slash commands:

**Content creation:** `create-post`, `create-article` (long-form), `create-dip`, `update-dip`, `build-voice-vocabulary`, `comment-on-post`, `reply-to-comments`, `find-comment-targets`

**Profile + planning:** `optimize-profile`, `post-publication`, `suggest-next-post`, `scan-telegram`, `weekly-update`

**Validation chain:** `validate-content`, `check-facts`, `check-generic`, `check-sources`, `detect-ai`

**LLM visibility:** `audit-llm-visibility`

Each one is a folder with a `SKILL.md` inside.

---

## FAQ

**Q: Do I have to use Claude Code Skills?**
No. Skills are just automation. You can apply the same methodology by hand: load the DIP into the prompt, follow the pipeline, check against the checklist.

**Q: Does it work for platforms other than LinkedIn?**
Yes. The architecture (DIP → Algorithm → Pipeline → Validation) is universal. Only the contents change: platform algorithm, formats, trends.

**Q: How many transcripts do I need for the first DIP?**
At least 1–2 for v0.5 (bootstrap). 3–4 for v0.7 (working). 5+ for v1.0 (production).

**Q: How often should I update the algorithm doc?**
Once a week for trends. Once a month for fundamental algorithm changes.

**Q: Can I use other people's posts as input for a DIP?**
No. Only raw sources (transcripts, voice input). Other people's output = someone else's voice + AI processing.
