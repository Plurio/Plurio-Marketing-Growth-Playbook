# How the algorithm knowledge system works

> Where the data comes from, how it's structured, how it's updated, and how it's used during content creation.

---

## Table of contents

1. [Overview: what the system knows](#overview)
2. [Data sources (where everything comes from)](#data-sources)
3. [Storage structure (where things live)](#storage-structure)
4. [LinkedIn Learning Transcripts — knowledge base](#linkedin-learning-transcripts--knowledge-base)
5. [How the data is updated](#how-the-data-is-updated)
6. [How the data is used during content creation](#how-the-data-is-used-during-content-creation)
7. [What to reuse for your own platform](#what-to-reuse-for-your-own-platform)

---

## Overview

The system maintains a **live knowledge base** of how LinkedIn ranks content. It's not a static document — the data is updated weekly and influences every post created.

**What the system knows:**

| Area | File | Lines | Updated |
|---------|------|-------|-------------|
| 360Brew ranking factors | Algorithm-Intelligence.md | ~430 | Monthly |
| Format benchmarks | Format-Performance-Data.md | — | Monthly |
| Posting time | Posting-Time-Guidelines.md | — | Monthly |
| Virality trends | Current-Trends.md | — | Weekly |
| Hook formulas | Hook-Pattern-Library.md | — | As discovered |
| Anti-patterns | Anti-Patterns.md | — | Monthly |
| Profile watchlist | Viral-Trends-Watchlist.md | — | Weekly |
| Formats (specs + performance) | Format-Catalog.md | — | Quarterly |
| Post performance | Performance-Log.md | — | After every post |
| Experiments | Experiment-Backlog.md | — | Weekly |
| Comments (algorithm + formulas) | Comments-Engine.md | — | Monthly |
| Profile optimization | Profile-Optimization-Guide.md | — | Quarterly |
| LinkedIn Learning courses (17 of them) | _LinkedIn-Learning-Transcripts/ | ~289K chars | Static |
| Benchmarks (competitors) | Benchmarks—Overview.md | — | Quarterly |

---

## Data sources

### A. Research (quantitative) — the foundation of everything

| Source | Authority | Data scale | Frequency | What it gives |
|----------|-----------|---------------|---------|---------|
| **Richard van der Blom** | Independent researcher | 1.8M posts, 58K profiles | Annually | Format performance, engagement-signal weights, reach trends |
| **AuthoredUp** | Analytics platform | 621K+ posts | Continuous | Median impressions, engagement rates, format benchmarks |
| **Buffer Analytics** | Social media platform | 2M+ posts (2025-2026) | Annually | Timing, frequency impact, format performance |
| **SocialInsider** | Analytics platform | Aggregated | Annually | Engagement benchmarks, format rankings |
| **LinkedIn Engineering Blog** | Official LinkedIn | — | Irregular (major updates) | 360Brew architecture, algorithm mechanics |
| **Hootsuite / Sprout Social / Agorapulse** | Platform vendors | Aggregated | Annually | Timing, frequency, format recommendations |

### B. Practitioner experts (qualitative)

| Source | Type | What it gives |
|----------|-----|---------|
| **Jasmin Alic** | LinkedIn expert | Hook strategies, content optimization, best practices |
| **Matt Navarra** | Social media analyst | First to report algorithm changes and platform updates |
| **Chris Donnelly** | Personal branding | Format experiments, growth tactics |
| **LinkedIn Official Blog** | Internal | Best practices, algorithm philosophy |
| **arXiv / Search Engine Land / MediaPost** | Academic + tech | 360Brew technical architecture |

### C. LinkedIn Learning courses (KEY SOURCE)

**17 transcribed courses** — roughly 289,000 characters in total. This isn't "just another source." It's the **foundation** for all recommendations on formats, profiling, branding, and content strategy.

**Full course list:**

| # | Course | Focus | What we extract |
|---|------|-------|--------------|
| 1 | Content Strategy in the Age of AI | AI tools, prompting, content workflows | How AI changes content creation; what to automate, what not to |
| 2 | Storytelling and Content Creation to Transform Your Personal Brand | Storytelling for personal brand | Narrative structures, hook formulas, emotional triggers |
| 3 | Social Media Marketing Strategy and Optimization | SMM strategy | General optimization principles, metrics, ROI |
| 4 | How to Stand Out on LinkedIn | LinkedIn-specific tactics | What works on the platform, what to avoid |
| 5 | Create LinkedIn Posts That Stand Out | Post creation | Specific writing techniques, formats, CTAs |
| 6 | Growing Your Business with LinkedIn Pages | Company pages | Personal vs. company differences, strategies for business pages |
| 7 | Strategies for Creating Viral Short-Form Content | Short-form content | Viral mechanics, attention economy, scroll-stopping techniques |
| 8 | Essential Skills for Social Media Managers | SMM management | Operational processes, tools, KPIs |
| 9 | Optimizing Your LinkedIn Profile (Nano Tips) | Profile | Headline, About, Experience optimization. Feeds `/optimize-profile` |
| 10 | Content Creation Strategy and Tools | Tools | Content creation workflow, planning, tooling |
| 11 | Personal Branding for People Who Hate the Spotlight | Low-stress branding | How to build a brand as an introvert. Useful for authors who are hard to engage |
| 12 | CMO's Guide to Engaging on LinkedIn | C-level engagement | Engagement specifics for executives. Feeds the DIP for C-level authors |
| 13 | B2B Marketing on LinkedIn | B2B | LinkedIn for B2B (our context is consumer, but the differences are worth knowing) |
| 14 | Executive's Guide to Engaging on LinkedIn | Executive branding | Executive tone, positioning, what works for founder content |
| 15 | How to Build a Strong Professional Brand on LinkedIn | Professional brand | Systematic approach to branding. Feeds the DIP concept |
| 16 | Marketing on LinkedIn | LinkedIn marketing | Paid + organic strategy |
| 17 | Rock Your LinkedIn Profile | Profile (advanced) | Advanced profile optimization techniques |

**Where stored:** `Skills/_LinkedIn-Learning-Transcripts/`

**How used:**
- Hook formulas → Hook-Pattern-Library.md
- Format recommendations → Format-Catalog.md, Algorithm-Intelligence.md
- Branding principles → Profile-Optimization-Guide.md, DIP concept
- Best practices → embedded across ALL reference files
- Validation → check-generic and detect-ai cross-check against this data

### D. Our own data (primary)

| Data | Where stored | Coverage |
|--------|-------------|---------|
| Post performance | Performance-Log.md | 5 authors (active authors) |
| DIP feedback logs | Inside each author's DIP | What worked / didn't for that specific author |
| Format experiments | Experiment-Backlog.md | Hypotheses + results |
| Engagement patterns | Comments-Engine.md | Patterns from real comments |

---

## Storage structure

All paths are relative to `Knowledge-Base/`.

```
Skills/
│
├── 02-LinkedIn-Algorithm/                  ← ALGORITHM
│   ├── Algorithm-Intelligence.md           ← Main file: 360Brew model, 8 factors,
│   │                                          engagement hierarchy, content lifecycle,
│   │                                          format performance, dead signals
│   ├── Format-Performance-Data.md          ← Raw benchmarks with sources
│   │                                          (Richard van der Blom 1.8M posts,
│   │                                           AuthoredUp 621K posts, Buffer 2M posts)
│   └── Posting-Time-Guidelines.md          ← Optimal times by timezone
│                                              (Tuesday 10AM consistently highest,
│                                               6-7AM LA for US + EU)
│
├── 03-Viral-Trends/                        ← TRENDS
│   ├── Current-Trends.md                   ← 4 categories: HOT NOW / RISING / DECLINING / DEAD
│   │                                          + industry-specific trends
│   ├── Hook-Pattern-Library.md             ← 7+ hook formulas with adaptation rules:
│   │                                          Data Shock, Contrarian, Transformation,
│   │                                          Behind the Scenes, Question-Led, List, Story
│   ├── Anti-Patterns.md                    ← Algorithm killers (pods, bait, stuffing)
│   │                                          Content killers (generic, buzzwords, walls)
│   │                                          Tone killers (bro-etry, corporate, passive)
│   └── Viral-Trends-Watchlist.md           ← 3 tiers of profiles to monitor:
│                                              Tier 1: Competitors (what they post)
│                                              Tier 2: Experts (what they recommend)
│                                              Tier 3: Viral masters (what takes off)
│
├── 05-Format-Testing/                      ← FORMATS
│   ├── Format-Catalog.md                   ← Specs for each format:
│   │                                          Carousel (1080x1350, 5-10 slides)
│   │                                          Text, Image, Video, Multi-image, Poll
│   │                                          + per-author affinity from the DIP
│   ├── Performance-Log.md                  ← Performance tracking for EVERY post:
│   │                                          Date | Hook | Format | Cluster |
│   │                                          Impressions | Likes | Comments | Saves
│   └── Experiment-Backlog.md               ← Active hypotheses to test
│
├── 06-Comments-Engine/                     ← COMMENTS
│   └── Comments-Engine.md                  ← Algorithmic weight of comments:
│                                              15+ words = 2.5x, reply <30 min = +64%,
│                                              5-10 comments/day = +20% reach on own posts
│                                              3 types × 5+ formulas each
│
├── 08-Profile-Optimization/                ← PROFILE
│   └── Profile-Optimization-Guide.md       ← 360Brew Profile-Content Alignment:
│                                              Photo = 3x connections, Verified = +60% views,
│                                              5+ skills = 2.9x views + 4.7x messages
│
├── 09-Visual-Design/                       ← DESIGN
│   ├── Visual-Design-System.md             ← Visual guidelines
│   └── Lovable-Carousel-Instructions.md    ← Instructions for carousel designs
│
├── _LinkedIn-Learning-Transcripts/         ← COURSES (17 of them)
│   ├── Content-Strategy-Age-of-AI.md
│   ├── Storytelling-Personal-Brand.md
│   ├── Social-Media-Marketing-Strategy.md
│   ├── How-to-Stand-Out-on-LinkedIn.md
│   ├── Create-LinkedIn-Posts-That-Stand-Out.md
│   ├── Growing-Business-LinkedIn-Pages.md
│   ├── Viral-Short-Form-Content.md
│   ├── Essential-Skills-SMM.md
│   ├── Optimizing-LinkedIn-Profile-Nano-Tips.md
│   ├── Content-Creation-Strategy-Tools.md
│   ├── Personal-Branding-Hate-Spotlight.md
│   ├── CMOs-Guide-LinkedIn.md
│   ├── B2B-Marketing-LinkedIn.md
│   ├── Executives-Guide-LinkedIn.md
│   ├── Build-Strong-Professional-Brand.md
│   ├── Marketing-on-LinkedIn.md
│   └── Rock-Your-LinkedIn-Profile.md
│
└── 07-Auto-Update/                         ← UPDATE PROCESS
    └── Weekly-Update-Workflow.md            ← Mon: Algorithm + Trends refresh
                                               Wed: Content scan (new transcripts)
                                               Fri: Performance review + planning
```

**Additional** (outside Skills/):

```
Content/your-benchmark-library/
└── Benchmarks—Overview.md                  ← Competitor benchmarks (17+ companies)
                                               Used by the Benchmark-Validation-System
```

---

## LinkedIn Learning Transcripts — knowledge base

### What it is

17 LinkedIn Learning courses, **fully transcribed** and saved as markdown files. Roughly 289,000 characters of text in total.

### Why it matters

These transcripts aren't just "useful links." They play 4 roles:

**1. Foundation for the reference files**

Algorithm-Intelligence.md, Format-Catalog.md, Profile-Optimization-Guide.md, Hook-Pattern-Library.md — all of these were built using data from these courses. Every recommendation in the reference files is backed either by quantitative research (van der Blom, Buffer) or by qualitative expertise from the courses.

**2. Skills training material**

When Claude Code runs `/create-post` or `/optimize-profile`, the reference files contain reprocessed knowledge from these courses. Not raw transcripts — a distilled version.

**3. Fallback source**

If a reference file doesn't cover a specific case (e.g., "how to write an About section for a C-level?"), Claude Code can go directly to the "Executive's Guide to Engaging on LinkedIn" transcript.

**4. Validation calibration**

`/check-generic` and `/detect-ai` cross-check content against best practices, some of which come from these courses. For example, the anti-pattern "text wall without whitespace" is from "Create LinkedIn Posts That Stand Out."

### How it works in the chain

```
LinkedIn Learning Course Transcripts (17 files, 289K chars)
         │
         ▼ processed and condensed into ▼
         │
Reference Files (Algorithm-Intelligence, Format-Catalog, Hooks, Anti-Patterns, Profile Guide)
         │
         ▼ loaded by skills ▼
         │
Skills (/create-post, /optimize-profile, /check-generic, /detect-ai, etc.)
         │
         ▼ produce ▼
         │
Content (posts, profiles, comments) + validation
```

### How to reuse this for your own platform

For another platform (X, YouTube, Telegram) — same approach:

1. **Find 10–20 courses/guides** from top experts on the platform
2. **Transcribe** (or copy the text)
3. **Save as markdown** in `_[Platform]-Learning-Transcripts/`
4. **Process** into reference files (Algorithm, Trends, Formats, Hooks)
5. **Refresh** weekly (trends) and monthly (foundation)

---

## How the data is updated

### Weekly cycle (`/weekly-update`)

| Day | What's updated | How | Time |
|------|----------------|-----|-------|
| **Monday** | Algorithm + Trends | WebSearch: "LinkedIn algorithm update 2026", Richard van der Blom, LinkedIn Engineering Blog. Cross-check: practitioner blogs (Jasmin Alic, Lara Acosta, Justin Welsh) | 45–60 min |
| **Wednesday** | Content (DIP, sources) | Scan 11 transcript locations. Extract: new stories, patterns, frameworks. Add ideas to the Topic Backlog | 30–45 min |
| **Friday** | Performance | Pull the week's metrics. Update Performance-Log. Close experiments. Review the Feedback Log: if one piece of feedback appears 3+ times → move it into the DIP | 30–45 min |

**Total: ~2–2.5 hours per week** to maintain the system.

### What specifically gets updated on Monday

**Algorithm-Intelligence.md:**
- New benchmarks → update the numbers
- New algorithm mechanics → update the description + changelog
- Changes to the engagement hierarchy → re-sort

**Current-Trends.md:**
- HOT NOW: what's new? what was confirmed?
- RISING: what moved from RISING to HOT? what new appeared?
- DECLINING: what dropped out of HOT?
- DEAD: what from DECLINING is now fully dead?

**Hook-Pattern-Library.md:**
- New formulas from observations + the watchlist

**Anti-Patterns.md:**
- New penalties from the algorithm

### Triggers for unscheduled updates

| Trigger | Action |
|---------|---------|
| LinkedIn Engineering Blog: major update | Immediate update to Algorithm-Intelligence |
| Richard van der Blom: new report | Update Format-Performance-Data + Algorithm-Intelligence |
| Sharp reach drop for one of our authors | Investigation: what changed? Update Anti-Patterns |
| New content type takes off in the feed | Update Current-Trends (RISING) |

---

## How the data is used during content creation

### When creating a post (`/create-post`)

```
User: /create-post Seva "AI agents replacing manual rules"

Claude Code loads:

1. Seva-Ustinov-DIP.md
   └── Tone of Voice: direct, no fluff, hook-first
   └── Cluster: AI-Native Teams (30%)
   └── Viral Angle: Contrarian take
   └── Stories Bank: "Built 150-person agency..."

2. Algorithm-Intelligence.md
   └── 360Brew: first sentence = anchor (disproportionate weight)
   └── Profile-Content Alignment: AI agents topic = in Seva's headline ✓
   └── Save-worthy > likes (5-10x)
   └── No links in first 300 chars
   └── 1200-1800 chars optimal

3. Current-Trends.md
   └── HOT NOW: AI tools + real results (not prompts, but outcomes)
   └── RISING: Semantic niche authority (90 days of consistency)
   └── DEAD: "5 agents every founder needs" listicles

4. Hook-Pattern-Library.md
   └── Pick: Contrarian hook
   └── Formula: "Everyone thinks [X]. They're wrong."
   └── Adapted to Seva: direct, no preamble

Claude Code decisions:

✓ Format: Text (carousel was 2 of the last 3 posts → rotate)
✓ Hook: "Most founders use AI agents to automate. That's the wrong starting point."
  (< 140 chars ✓, contrarian ✓, Seva's tone ✓)
✓ Length: 1,450 chars (within optimal range)
✓ CTA: specific question, not "agree?"
✓ No links in the first 300 chars
✓ Cluster: AI-Native Teams (not overloaded: 30% target vs 28% actual)
```

### During validation (`/validate-content`)

```
/check-generic loads:
  └── Anti-Patterns.md → checks: no engagement bait? no bro-etry?
  └── Algorithm-Intelligence.md → profile-content alignment?
  └── Last 10 posts → hook repeats? cluster imbalance?

/detect-ai loads:
  └── Algorithm-Intelligence.md → does the structure help or hurt 360Brew parsing?
  └── Verdict: em-dash overuse → reduce to 1 per 8 sentences
```

### When commenting (`/comment-on-post`)

```
Comments-Engine.md provides:
  └── Min 15 words (2.5x algorithm weight)
  └── Reply <30 min = +64% total comments
  └── Formula: "Curious about [specific]" (Ask smart question)

Algorithm-Intelligence.md provides:
  └── Comments train the profile: what you comment on = what you get shown
  └── Thread depth weighted higher than isolated comments
```

### During profile optimization (`/optimize-profile`)

```
Algorithm-Intelligence.md provides:
  └── 360Brew cross-checks content vs profile → semantic mismatch = suppressed
  └── Headline keywords should match post topics

Profile-Optimization-Guide.md (from LinkedIn Learning courses) provides:
  └── Photo = 3x connections, 2x profile views
  └── 5+ skills = 2.9x views, 4.7x messages
  └── Verified = +60% profile views
  └── Headline: first 60 chars visible in feed → most important first
```

---

## What to reuse for your own platform

### Data model (universal)

This model works for ANY platform:

```
┌─────────────────────────────────────────┐
│  KNOWLEDGE BASE (courses, transcripts)  │
│  10-20 expert courses/guides            │
│  Transcribed → markdown                 │
└────────────────┬────────────────────────┘
                 │ process + condense
┌────────────────┴────────────────────────┐
│  REFERENCE FILES (living documents)      │
│  Algorithm-Intelligence (factors)        │
│  Format-Performance-Data (benchmarks)    │
│  Current-Trends (what works)             │
│  Hook/Opening-Pattern-Library            │
│  Anti-Patterns (what gets penalized)     │
│  Comments/Engagement-Engine              │
└────────────────┬────────────────────────┘
                 │ loaded by skills
┌────────────────┴────────────────────────┐
│  SKILLS (automation)                     │
│  /create-content → /validate-content     │
│  /weekly-update (maintenance)            │
└────────────────┬────────────────────────┘
                 │ produce
┌────────────────┴────────────────────────┐
│  PERFORMANCE DATA (feedback)             │
│  Performance-Log (per-post metrics)      │
│  Experiment-Backlog (hypotheses)         │
│  DIP Feedback Logs (what worked)         │
└─────────────────────────────────────────┘
         ↑ feeds reference-file updates
```

### Step-by-step adaptation

**Step 1: Courses / Knowledge Base (2–3 days)**

For your platform (X, YouTube, Telegram, TikTok):
1. Find 10–20 of the best courses/guides from platform experts
2. Transcribe (or copy them)
3. Save in `_[Platform]-Learning-Transcripts/`

Examples:
- **YouTube:** vidIQ Academy, Think Media, Channel Makers courses
- **X/Twitter:** Justin Welsh's thread playbook, Dickie Bush, Dan Koe
- **Telegram:** Russian-language SMM courses, channel case studies
- **TikTok:** Keenya Kelly, Wave Wyld, Later's guides

**Step 2: Reference Files (1–2 days)**

Process the knowledge base into living documents:

| File | For what | How to fill |
|------|---------|--------------|
| Algorithm-Intelligence.md | Ranking factors | From courses + the platform's official blogs |
| Format-Performance-Data.md | Benchmarks | From research + your own data |
| Current-Trends.md | What works / dies | From observations + experts |
| Hook-Pattern-Library.md | Opening formulas | From courses + your own analysis |
| Anti-Patterns.md | What gets penalized | From courses + experts + your own experience |

**Step 3: Weekly Update process (set the rhythm)**

At minimum:
- Once a week: trends (what's new? what died?)
- Once a month: foundation (ranking factors, benchmarks)
- After every post: performance

**Step 4: (Optional) Skills**

If you use Claude Code — adapt the skills. If not — the same reference files work as prompts: load Algorithm-Intelligence + DIP + Trends into any AI and ask it to create content.

---

## Key numbers (what the system knows about LinkedIn today)

### 8 360Brew ranking factors (March 2026)

| # | Factor | Weight | Rule |
|---|--------|-----|---------|
| 1 | Profile-Content Alignment | Critical | Headline/About MUST match post topics |
| 2 | Topic Consistency | Critical | 90 days in 3–4 clusters = semantic authority |
| 3 | First Sentence Anchor | Critical | The first line gets disproportionate weight ("Lost-in-Distance" effect) |
| 4 | Saves > Likes | Very High | 1 save = 5–10 likes in weight |
| 5 | Comments Train Profile | High | What you comment on = what you get shown |
| 6 | Links = Penalty | High | ~60% reach loss. "Link in first comment" is also penalized (2026) |
| 7 | Structure Aids AI | Medium | Short paragraphs, lists → 360Brew parses semantics better |
| 8 | Hashtags = Minimal | Low | 1–3 max. 360Brew understands context without them. 5+ = spam risk |

### Engagement hierarchy

| Action | Weight vs baseline |
|----------|----------------|
| Saves | 5–10x |
| DM shares | ~5x |
| Reposts from influential | ~4x |
| Comments 15+ words | 2.5x |
| Thread depth | Variable, high |
| Dwell time 31–60 sec | High |
| Comments (any) | 2x |
| "See more" click | Medium-high |
| Likes | 1x (baseline) |
| "Great post!" comments | Downranked |

### Format performance (engagement rate)

| Format | Engagement Rate | 2026 trend |
|--------|----------------|------------|
| Carousel/Document | 6.60% | Stable-high (generic declining) |
| Multi-Image | 6.60% | Stable, underutilized |
| Native Video | 5.60% | Growing +23% YoY |
| Text Only | 2–4% | Declining -18% YoY |
| Polls | Declining | Multiplier 1.64x → 1.19x |
| External Links | ~60% penalty | Penalized |

### Timing

| Parameter | Optimum |
|----------|---------|
| Best day | Tuesday 10 AM |
| Best window (US + EU overlap) | 6–7 AM LA time |
| Frequency sweet spot | 3–5 posts/week |
| 2+ posts/day penalty | -40%+ reach per post |
| No new post within | 12 hours of previous |
