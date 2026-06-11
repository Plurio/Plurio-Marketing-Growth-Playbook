# LinkedIn Growth Loop — System Architecture

> **What this is:** an anonymized architecture for a closed-loop LinkedIn growth system. Each stage feeds the next: what you WANT (targets) → what you DO (create) → what you COLLECT (data) → what you UNDERSTAND (analyze) → how you ADJUST (adjust) → next cycle.
>
> **When to use:** when you want more than just "writing posts" — you want systematic growth (followers, ER, subscription conversion) with feedback between metrics and content strategy.
>
> **Companion document:** `Growth-Plan-Template.md` — concrete target model and formulas for Google Sheets.

---

## The Loop

```
┌──────────────────────────────────────────────────────────────────┐
│                                                                  │
│   ① TARGETS          ② CREATE             ③ COLLECT              │
│   (what we want) →   (create content) →   (collect data)         │
│                                                                  │
│   Spreadsheet         Post-Creation         Stats scraper        │
│   Growth Plan         Engine + DIP          + dashboard sync     │
│                                                                  │
│         ↑                                          ↓             │
│                                                                  │
│   ⑤ ADJUST           ④ ANALYZE                                   │
│   (change approach) ← (compare actual/plan)                      │
│                                                                  │
│   Algorithm Intel     Monthly Review                             │
│   Format Strategy     Performance Log                            │
│   DIP feedback        Gap Analysis                               │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

---

## ① TARGETS — what we want

**Source of truth:** one table (Google Sheet / Excel / Airtable). Metrics are split into:

- **INPUT rates** (what WE move through actions) — Save Rate, Comment Rate, Reaction Rate, Repost Rate, Follow Conversion, Posts.
- **FORMULA metrics** (computed from INPUT) — ER, Impressions/Post, Impressions, Engagement counts, New Followers, Total Followers.

See the full INPUT vs FORMULA list in `Growth-Plan-Template.md`.

### When to revise targets

- **Monthly:** actual vs plan; adjust INPUT rates for the next quarter.
- **When the platform algorithm changes:** recompute base reach and quality multiplier.
- **When a new benchmark appears from external sources:** update baseline ER, Save Rate.

---

## ② CREATE — create content

**Engine:** `/create-post [Author]` → `Knowledge-Base/04-Post-Creation-Engine/Post-Creation-Engine.md`.

### How targets influence creation

| What is underperforming in the plan | What we change in content |
|---------------------------|-----------------------|
| Save Rate < target | More carousels, frameworks, step-by-step, templates |
| Comment Rate < target | Questions at the end, controversial takes, "how about you?" |
| Reaction Rate < target | Stronger hooks, contrarian first line |
| Reposts < target | Share-worthy data, original benchmarks |
| Saves/Post < 10 | Content isn't actionable enough — add templates |
| Carousel % < target | Plan 2-3 carousels for next week |
| Follow Conversion < target | Profile audit, headline-content alignment, newsletter CTA |

### Files the Post Creation Engine reads

```
① Growth Plan targets       → determines format PRIORITY ("which rate is lagging?")
② Author DIP                → determines TONE and TOPIC
③ Algorithm Intelligence    → determines post STRUCTURE
④ Performance Log           → determines WHAT WORKS based on historical data
⑤ Current Trends            → determines RELEVANCE
```

### Rule: every post must work toward a specific target

Before writing a post, check the Growth Plan: which INPUT rate is currently lagging behind plan? This post = a tool to pull up exactly that metric.

---

## ③ COLLECT — collect data

### What and from where

| What | Source | Frequency | Notes |
|-----|----------|---------|---------|
| Per-post metrics (Impressions, Reactions, Comments, Reposts) | LinkedIn API | Monthly | Available via REST API with Marketing Developer Platform access |
| Dashboard totals (Saves, Sends, New Followers, Total) | LinkedIn UI scraper | Monthly | Saves and Sends are NOT available via API — dashboard only |
| Per-post content meta (format, hook, topic) | Manual / parsing your Posted/ archive | Monthly | Needed to correlate "format → impressions" |
| External benchmarks | Industry reports + topical research | Quarterly | Baseline for comparison |

### What to collect per post

- Date, hook text, format (text / carousel / image / video / collab).
- Impressions, reactions, comments, reposts, **saves** (manual), **sends** (manual).
- Cluster / topic / editorial pillar (for analytic mix).

### What you can't get from API alone

- **Saves** and **Sends** in LinkedIn UI are aggregated by account, not per post. Per-post saves are either collected manually or estimated: `avg_saves = total_saves / posts`.
- **Format auto-detection** — needs logic like "if a post has a document → carousel".

---

## ④ ANALYZE — compare

### Monthly Review Dashboard

Five key metrics to check EVERY month:

| # | Metric | What it shows | Where to aim |
|---|---------|---------------|-----------------|
| 1 | **Follow Conversion Rate** | How well content drives follows | 1.0-1.5%+ |
| 2 | **Save Rate** | Content quality (main leading indicator for the algorithm) | 0.15-0.25%+ |
| 3 | **Engagement Rate** | Overall engagement | 2.5-3.5%+ |
| 4 | **Saves/Post** | Save rate per individual post | 15-20+ |
| 5 | **MoM Growth %** | Growth pace (should accelerate when compound loop is working) | 15-25%+ |

### Gap Analysis (automatic)

For each metric: `gap% = (Actual − Target) / Target × 100%`.

| Gap signal | What it means | What we do |
|-----------|----------------|------------|
| ER below plan by 20%+ | Content isn't resonating | Revisit topics, check hooks |
| Save Rate < plan | Not actionable enough | More carousels, frameworks |
| Comment Rate < plan | Low engagement | Strengthen commenting routine + questions |
| Follow Conv < plan | Profile doesn't convert | Profile audit, headline alignment |
| Saves/Post < 10 | Posts are being scrolled past | Every post = framework / template |
| MoM Growth slowed | Compound loop isn't working | Check all rates + consider paid boost |

### Per-Post Patterns

From the accumulated Performance Log we identify:

```
Best performers (top 3 / month by impressions):
  → What format? → What hook? → What topic?
  → Record the pattern in Algorithm Intelligence

Worst performers (bottom 3):
  → What didn't work? → Topic? Format? Time?
  → Record the anti-pattern

Content Mix analysis:
  → Carousel avg impressions vs Text avg impressions
  → If the gap is >1.5x — increase share of the winning format
```

---

## ⑤ ADJUST — change approach

After analysis, the following are updated:

| Document | What we update | When |
|----------|---------------|-------|
| **Spreadsheet INPUT rates** | Adjust targets if unrealistic (or, conversely, too low) | Monthly review |
| **Algorithm-Intelligence.md** | New patterns from per-post data | Monthly + ad-hoc when insights emerge |
| **Performance-Log.md** | New month's data | After collection |
| **Current-Trends.md** | What works now (internal + external) | Monthly |
| **DIP Feedback Log** | Feedback on specific posts | After every post |
| **Post-Creation-Engine.md** | If format strategy has changed | Quarterly |
| **Growth Plan formulas** | Base reach / quality weights recomputed against actual data | Quarterly after 3+ months |

### Recalculation formula (once 3+ months of data accumulate)

```
Actual base_reach = AVG(Impressions/Post per quarter) / AVG(Total Followers)
Actual Save Rate impact = correlation(Save Rate, Impressions/Post month-over-month)
```

After this — update the `Impressions/Post` formula in the Spreadsheet with the new coefficients.

---

## Slash commands (workflow)

| Command | What it does | When |
|---------|------------|-------|
| `/monthly-review [Author]` | Collects data → compares to targets → gap analysis → recommendations | 1st of the month |
| `/suggest-next-post [Author]` | Reads gaps + Performance Log → recommends topic + format | Before every post |
| `/weekly-update` | Algorithm refresh + content scan + performance pulse | Every Monday |
| `/create-post [Author]` | Creates a post taking into account current gap signals from the Growth Plan | On demand |

### `/monthly-review` — typical workflow

```
1. Collect data:
   - Stats puller (API) → per-post JSON
   - Dashboard scraper → totals (saves, sends, new followers)

2. Load into Spreadsheet:
   - Sync script → actuals into rows by month

3. Compare actual vs target:
   - Read Sheet: actual vs plan for each metric
   - Compute gap% for each

4. Per-post analysis:
   - Top/bottom 3 posts of the month
   - Content mix (% carousel vs text vs video)
   - What do the best posts have in common? The worst?

5. Recommendations:
   - Which rate is lagging → what to do in content
   - Which format is working → more of that
   - Which topics resonate → prioritize in Topic Backlog

6. Update documents:
   - Performance Log → month's data
   - Algorithm Intelligence → new patterns
   - Growth Plan → adjust targets for next quarter (if needed)
```

---

## File map (how everything connects)

```
Spreadsheet (Google Sheet / Excel / Airtable)
  ├── Facts (historical data)       ← stats puller + scraper
  ├── Targets (plan)                ← Growth Plan model
  └── Growth Levers (paid, newsletter, podcasts, ...)

Growth-Plan-Template.md
  ├── Causal model: INPUT rates → formulas → followers
  ├── Quarterly targets (= Spreadsheet targets)
  └── Phase strategy (Foundation / Acceleration / Scale / Sprint)

Growth-Loop-Architecture.md (THIS FILE)
  └── Architecture: how everything connects

Knowledge-Base/
  ├── 01-... DIP (Digital Identity Profile)
  │     └── Feedback Log ← updated after every post
  ├── 02-LinkedIn-Algorithm/Algorithm-Intelligence.md
  │     └── Updated monthly + when new patterns appear
  ├── 03-Viral-Trends/Current-Trends.md
  │     └── Updated monthly
  ├── 04-Post-Creation-Engine/Post-Creation-Engine.md
  │     └── Reads: DIP + Algorithm + Trends + Performance Log + Growth Plan gaps
  ├── 05-Format-Testing/Performance-Log.md
  │     └── Populated from stats puller per-post data
  └── 07-Auto-Update/Weekly-Update-Workflow.md
        └── Performance pulse from this loop

scripts/  (your tooling — not provided here)
  ├── linkedin_stats              → per-post API data
  ├── linkedin_dashboard_scraper  → dashboard totals via headless browser
  └── spreadsheet_sync            → push facts to Sheet
```

---

## Minimal set-up (if no API access)

The loop works WITHOUT automated collection if you're willing to manually copy dashboard numbers once a month. Minimum:

1. **Spreadsheet** with 5 key metrics × 12 months.
2. **Posted/[Author]/YYYY-MM-DD-[slug].md** for each post with meta (format, hook, topic).
3. **30 minutes once a month** — copy Impressions / ER / Saves / New Followers from LinkedIn Analytics + fill out Performance Log.

Without this minimum, the loop won't close and optimization will be intuitive rather than data-driven.
