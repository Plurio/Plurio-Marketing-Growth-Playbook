# LinkedIn Growth Plan — Template (Causal Model + Quarterly Targets)

> **What this is:** an anonymized Growth Plan template for an individual LinkedIn account. Contains the causal model of metrics, formulas for Google Sheets, phase strategy, and monthly tables.
>
> **How to use:** copy into your repo, plug in your baselines and targets, fill the Spreadsheet using the formulas below. Companion document — `Growth-Loop-Architecture.md` (describes how this plan fits into the closed loop).
>
> **Target audience:** founder / executive / senior IC who wants to grow a personal LinkedIn account to 50K–100K followers in 12–18 months on organic + moderate paid boost.

---

## 1. How to extend your spreadsheet

### Base columns (usually already in LinkedIn Analytics)

```
Posts | Impressions | Members reached | Social Engagements |
Reactions | Comments | Reposts | Saves | Sends on LinkedIn |
Link engagements | Premium custom button interactions |
Engagement Rate | New Followers | Total followers
```

### What to add (new rows)

```
═══════════════════════════════════════════════════════════════
ADD — Per Post Averages (formulas)
═══════════════════════════════════════════════════════════════
Impressions/Post          = Impressions / Posts
Engagements/Post          = Social Engagements / Posts
Comments/Post             = Comments / Posts
Saves/Post                = Saves / Posts
New Followers/Post        = New Followers / Posts

═══════════════════════════════════════════════════════════════
ADD — Conversion Rates (key for forecasting)
═══════════════════════════════════════════════════════════════
Engagement Rate           = Social Engagements / Impressions × 100%
Follow Conversion Rate    = New Followers / Impressions × 100%
                            ← THE PRIMARY metric for growth forecasting
Save Rate                 = Saves / Impressions × 100%
                            ← content quality indicator
Comment Rate              = Comments / Impressions × 100%
                            ← engagement indicator

═══════════════════════════════════════════════════════════════
ADD — Content Mix (what we publish)
═══════════════════════════════════════════════════════════════
Posts: Text only           = number of text posts
Posts: Carousel            = number of carousels
Posts: Image/Multi-image   = number of posts with images
Posts: Video               = number of videos
Posts: Collaboration       = number of collabs with other authors
Newsletter issues          = number of newsletter issues
Newsletter subscribers     = subscribers (LinkedIn auto-equates to followers)

═══════════════════════════════════════════════════════════════
ADD — Growth Levers (what drives growth beyond posts)
═══════════════════════════════════════════════════════════════
Outbound comments (5+/day) = number of days with active commenting
Paid spend ($)             = boost budget
Podcast/Event appearances  = number of external appearances
Cross-platform mentions    = LinkedIn mentions in Telegram/X/email
```

---

## 2. Baselines (fill in yourself)

> **First** — collect 3 months of your own actuals from LinkedIn Analytics to understand your starting point. Without a baseline, the model can't be calibrated.

| Metric | Where to get it | Type |
|---------|--------------|-----|
| Posts | LinkedIn Analytics → Content | INPUT |
| Impressions | LinkedIn Analytics → Content | FORMULA-derived |
| Reactions / Comments / Reposts | LinkedIn Analytics → Content (per post) | FORMULA-derived |
| Saves / Sends | LinkedIn Analytics → Dashboard (UI only, not API) | Manual |
| Members Reached | LinkedIn Analytics → Audience | ≈ 0.65–0.70 × Impressions |
| New Followers | LinkedIn Analytics → Audience | Manual / delta |
| Total Followers | LinkedIn API / profile | API |

### Typical "starting point" diagnosis

On your first measurement, you'll most likely see:
- **ER:** 0.5–1.5% — normal range for an unfocused account.
- **Save Rate:** 0.02–0.05% — almost always low, because the content isn't actionable.
- **Follow Conversion:** 0.3–0.7% — normal for generic content; for focused content it will rise to 1.0–1.5%.
- **Distribution:** 1–2 posts generate 60–80% of all impressions (viral); the rest are baseline.

If your numbers are significantly lower — check profile-content alignment (headline vs. "all over the place" post topics); if significantly higher — you already have a working account and can jump straight to the Acceleration phase.

---

## 3. Quarterly targets — interconnected model

### Causal model (how metrics relate)

```
╔══════════════════════════════════════════════════════════════╗
║  LAYER 1: WHAT WE CONTROL (actions)                          ║
║  ┌──────────┐  ┌────────────┐  ┌─────────────┐               ║
║  │ Posts    │  │Content Mix │  │ Commenting  │               ║
║  │ (count)  │  │(% carousel)│  │ (routine)   │               ║
║  └────┬─────┘  └─────┬──────┘  └──────┬──────┘               ║
╚═══════╪══════════════╪════════════════╪═══════════════════════╝
        │              │                │
        │              ▼                ▼
╔═══════╪══════════════════════════════════════════════════════╗
║  LAYER 2: QUALITY METRICS (leading indicators)               ║
║              ┌────────────┐  ┌─────────────┐                 ║
║              │ Save Rate  │  │Comment Rate │                 ║
║              │ (⬅ INPUT)  │  │ (⬅ INPUT)   │                 ║
║              └─────┬──────┘  └──────┬──────┘                 ║
║                    │                │                         ║
║              ┌─────▼────────────────▼──────┐                 ║
║              │      ER (computed)          │                 ║
║              │ = Save + Comment + Reaction │                 ║
║              │   + Repost rates             │                 ║
║              └──────────────┬──────────────┘                 ║
╚═════════════════════════════╪════════════════════════════════╝
                              │
                              ▼
╔═════════════════════════════════════════════════════════════════╗
║  LAYER 3: ALGORITHM RESPONSE (Impressions/Post)                ║
║                                                                 ║
║  Impressions/Post = f(Total Followers, ER, Save Rate)          ║
║                                                                 ║
║  Imp/Post = Followers × BASE_REACH × (1 + QUALITY_BOOST)       ║
║                                                                 ║
║  where BASE_REACH is calibrated from your 3 months of data     ║
║  where QUALITY_BOOST depends on ER and Save Rate               ║
║                                                                 ║
║  This is the key formula: quality → algorithm shows the post   ║
║  to more people → impressions grow                             ║
╚═══════════════════════════════════╪═════════════════════════════╝
                                    │
                                    ▼
╔═════════════════════════════════════════════════════════════════╗
║  LAYER 4: REACH                                                ║
║  Impressions = Posts × Impressions/Post                        ║
╚═══════════════════════════════════╪═════════════════════════════╝
                                    │
                                    ▼
╔═════════════════════════════════════════════════════════════════╗
║  LAYER 5: ENGAGEMENT (absolute numbers)                        ║
║  Reactions = Impressions × Reaction Rate                       ║
║  Comments  = Impressions × Comment Rate                        ║
║  Saves     = Impressions × Save Rate                           ║
║  Reposts   = Impressions × Repost Rate                         ║
║  Social Engagements = sum of above                             ║
╚═══════════════════════════════════╪═════════════════════════════╝
                                    │
                                    ▼
╔═════════════════════════════════════════════════════════════════╗
║  LAYER 6: GROWTH                                               ║
║  New Followers = Impressions × Follow Conversion               ║
║  Total Followers = Previous Total + New Followers              ║
╚═══════════════════════════════════╪═════════════════════════════╝
                                    │
                        ╭───────────╯
                        │ FEEDBACK LOOP
                        ▼
         Total Followers (N+1) → Impressions/Post (N+1) grows
         (compound growth: more followers = higher reach base)
```

### INPUT vs FORMULA (for Google Sheets)

| Parameter | Type | Why |
|----------|-----|--------|
| **Posts** | ⬅ INPUT | You decide how many you publish |
| **Save Rate** | ⬅ INPUT-target | Driven by content mix (carousels, frameworks) |
| **Comment Rate** | ⬅ INPUT-target | Driven by commenting routine + questions in posts |
| **Reaction Rate** | ⬅ INPUT-target | Driven by hooks + contrarian takes |
| **Repost Rate** | ⬅ INPUT-target | Driven by share-worthy content |
| **Follow Conversion** | ⬅ INPUT-target | Driven by profile optimization + newsletter |
| | | |
| **ER** | 📐 FORMULA | `= Save Rate + Comment Rate + Reaction Rate + Repost Rate` |
| **Impressions/Post** | 📐 FORMULA | `= Prev_Followers × BASE_REACH × (1 + ER_Boost + Save_Boost)` |
| **Impressions** | 📐 FORMULA | `= Posts × Impressions/Post` |
| **Reactions** | 📐 FORMULA | `= Impressions × Reaction Rate` |
| **Comments** | 📐 FORMULA | `= Impressions × Comment Rate` |
| **Saves** | 📐 FORMULA | `= Impressions × Save Rate` |
| **Reposts** | 📐 FORMULA | `= Impressions × Repost Rate` |
| **Social Engagements** | 📐 FORMULA | `= Reactions + Comments + Saves + Reposts` |
| **All /Post averages** | 📐 FORMULA | `= [Metric] / Posts` |
| **New Followers** | 📐 FORMULA | `= Impressions × Follow Conversion` |
| **Total Followers** | 📐 FORMULA | `= Previous Quarter Total + New Followers` |

### Key formula — Impressions/Post

```
Impressions/Post = Total_Followers(prev) × BASE_REACH × QUALITY_MULTIPLIER

BASE_REACH       — calibrated from your data
                   = average(Impressions/Post) / average(Total Followers)
                   over 3+ months of history
                   (typical values: 0.8 – 1.5 for 5K–50K accounts)

QUALITY_MULTIPLIER = 1 + ER_Boost + Save_Boost

ER_Boost     = (ER / Baseline_ER − 1) × 0.5
               Baseline_ER = your current ER at the time of calibration
               If ER grew 2x → Impressions/Post +50%

Save_Boost   = (Save_Rate / Baseline_Save_Rate − 1) × 0.3
               Baseline_Save_Rate = your current Save Rate
               If Save Rate grew 3x → Impressions/Post +60%
               (saves carry 5–10x weight in the LinkedIn algorithm,
                so the boost coefficient is stronger)
```

> **Important:** the 0.5 and 0.3 coefficients are an empirical guess. After 3 months working with this model — recompute them via correlation between your actuals and the forecast, then update the formula.

---

## 4. Phase strategy

| Phase | Period | Main lever | Action | Effect |
|------|--------|---------------|----------|--------|
| **Foundation** | Months 1–3 | Save Rate + Comment Rate | 30% carousels, daily commenting routine, a framework in every second post | ER grows → Imp/Post grows via Quality Multiplier |
| **Acceleration** | Months 4–6 | Compound loop (followers → reach) | Double posting frequency; more collabs | Imp/Post jumps due to compound effect |
| **Scale** | Months 7–9 | Follow Conversion + paid | Newsletter, paid boost on best posts, podcast appearances | More followers at the same reach |
| **Sprint** | Months 10–12 | Everything together | All levers at max, cross-platform amplification | Compound loop accelerates exponentially |

### Feedback loop — why growth accelerates

```
Phase 1: A followers × BASE × 1.0 quality = X imp/post
Phase 2: B followers × BASE × 1.4 boost  = ~1.4X imp/post
Phase 3: C followers × BASE × 1.3 boost  = ~2X+ imp/post  ← followers 2x = imp/post 2x
Phase 4: D followers × BASE × 1.2 boost  = ~3X+ imp/post  ← quality boost slows,
                                                              but follower compound = growth
```

Quality boost slows down (diminishing returns from ER), but **follower compound** more than compensates. The key insight: **the initial growth in ER and Save Rate kicks off the flywheel, then compound does the work.**

---

## 5. Spreadsheet structure (for Google Sheets / Excel)

### Tab 1: Monthly Actuals vs Plan

```
| Metric                   | M1 ACTUAL | M1 PLAN | M2 ACTUAL | M2 PLAN | ...
|--------------------------|-----------|---------|-----------|---------|
| VOLUME                   |           |         |           |         |
| Posts                    |           |         |           |         |
|   Text only              |           |         |           |         |
|   Carousel               |           |         |           |         |
|   Image/Multi-image      |           |         |           |         |
|   Video                  |           |         |           |         |
|   Collaboration          |           |         |           |         |
|                          |           |         |           |         |
| REACH                    |           |         |           |         |
| Impressions              |           |         |           |         |
| Members Reached          |           |         |           |         |
| Impressions/Post         |           |         |           |         |
|                          |           |         |           |         |
| ENGAGEMENT               |           |         |           |         |
| Social Engagements       |           |         |           |         |
| Reactions                |           |         |           |         |
| Comments                 |           |         |           |         |
| Reposts                  |           |         |           |         |
| Saves                    |           |         |           |         |
| Sends                    |           |         |           |         |
|                          |           |         |           |         |
| PER POST AVERAGES        |           |         |           |         |
| Engagements/Post         |           |         |           |         |
| Comments/Post            |           |         |           |         |
| Saves/Post               |           |         |           |         |
|                          |           |         |           |         |
| CONVERSION RATES         |           |         |           |         |
| Engagement Rate (ER)     |           |         |           |         |
| Follow Conversion Rate   |           |         |           |         |
| Save Rate                |           |         |           |         |
| Comment Rate             |           |         |           |         |
|                          |           |         |           |         |
| GROWTH                   |           |         |           |         |
| New Followers            |           |         |           |         |
| Total Followers          |           |         |           |         |
| MoM Growth %             |           |         |           |         |
|                          |           |         |           |         |
| NEWSLETTER               |           |         |           |         |
| Newsletter issues        |           |         |           |         |
| Newsletter subscribers   |           |         |           |         |
|                          |           |         |           |         |
| GROWTH LEVERS            |           |         |           |         |
| Active commenting days   |           |         |           |         |
| Collaborations           |           |         |           |         |
| Podcast appearances      |           |         |           |         |
| Paid spend ($)           |           |         |           |         |
| Cross-platform CTAs      |           |         |           |         |
```

### Tab 2: Quarterly Summary Dashboard

```
| Quarter | Posts | Impressions | ER | Saves | Follow Conv | New Followers | Total |
|---------|-------|-------------|----|----|----|----|----|
| Q1      |       |             |    |       |             |               |       |
| Q2      |       |             |    |       |             |               |       |
| Q3      |       |             |    |       |             |               |       |
| Q4      |       |             |    |       |             |               |       |
```

---

## 6. Tasks for the content creator (standard cadence of 16–20 posts/month)

### Weekly rhythm

| Day | Format | Time (your TZ) | Content |
|------|--------|----------------|---------|
| **Tuesday** | Carousel | morning peak | Framework / How-to / Data |
| **Wednesday** | Text | morning peak | Contrarian take / Story |
| **Thursday** | Carousel or Video | morning peak | Deep-dive / Behind-the-scenes |
| **Friday (opt.)** | Text or Multi-image | a bit later | Quick insight / Screenshot |

> **Time:** see `Knowledge-Base/02-LinkedIn-Algorithm/Posting-Time-Guidelines.md` for determining your optimal posting time based on audience time zones.

### Content mix targets (% of total)

| Format | Phase 1 | Phase 2 | Phase 3–4 | Why |
|--------|---------|---------|-----------|--------|
| Carousel | 30–35% | 40–50% | 50% | High ER + saves — the main growth driver |
| Text | 45–50% | 30% | 25% | Dwell time, personal stories |
| Video | 5–10% | 10–15% | 15% | Authenticity, personal connection |
| Multi-image | 10% | 10% | 10% | Screenshots, data, before/after |

### Save priorities (the most important signal for the algorithm)

Saves grow from content people want to revisit:

1. **Frameworks** — "Here's my exact process for X" (carousel)
2. **Data** — original numbers, comparisons, benchmarks
3. **Templates** — checklists, decision trees, formulas
4. **Step-by-step** — concrete instructions with results
5. **Contrarian + proof** — "Everyone does X, here's why Y works better" + data

### Commenting routine (required every workday)

| Time | Action | Count |
|-------|----------|--------|
| Morning (before your post) | Comments on posts from major accounts in your niche | 3–5 |
| After publishing | Reply to all comments under your post | All within the first 30 min |
| Evening | Comments on trending posts in your vertical | 3–5 |

**Rules:** 15+ words per comment. Add value, not "Great post!". Use it as an entry point to your profile — the algorithm will show your comment to the other post's audience.

### Newsletter (if you launch one)

- **Frequency:** once a week (midweek).
- **Format:** top insights of the week + 1 deep-dive.
- **Goal:** every subscriber = an automatic LinkedIn follower.
- **Growth pattern:** typically 5–10% of followers subscribe to the newsletter in the first month after launch.

---

## 7. KPI dashboard for monthly review

Every month, check 5 key metrics:

| # | Metric | What it shows | How to compute | Target range |
|---|---------|----------------|-------------|------------------|
| 1 | **Follow Conversion Rate** | Attractiveness for following | New Followers / Impressions | 1.0–1.5%+ |
| 2 | **Save Rate** | Content quality (for the algorithm) | Saves / Impressions | 0.15–0.25%+ |
| 3 | **ER** | Overall engagement | Engagements / Impressions | 2.5–3.5%+ |
| 4 | **Saves/Post** | Quality of each individual post | Saves / Posts | 15–20+ |
| 5 | **MoM Growth %** | Growth pace (should accelerate) | New / Previous Total × 100 | 15–25%+ |

### Signals that the plan is working

- ER grows every month.
- Save Rate grows (the main leading indicator).
- Follow Conversion > 1%.
- Carousels consistently deliver 1.5–3x average impressions.

### Signals you need to adjust

- ER falling for 2 months in a row → revisit topics and formats.
- Saves aren't growing → content isn't actionable enough, add frameworks.
- Follow Conversion falling → check Profile-Content Alignment (headline vs. post topics).
- Impressions growing but ER falling → content has gone generic, return to specificity.

---

## 8. Budget (paid acceleration — optional)

| Period | Monthly budget | Spend on | Expected ROI |
|--------|-----------------|--------|---------------|
| Months 1–2 | $0–300 | Test: boost the best carousel | Baseline to learn whether paid works for you |
| Months 3–6 | $500–1,000 | Top 2–3 posts/mo + follower ads | +30–50% on top of organic growth |
| Months 7–10 | $1,000–1,500 | Scale what worked | +40–60% on top of organic growth |
| Months 11–12 | $1,500–2,000 | Sprint to target followers | +50% on top of organic growth |

**Total over 12 months:** $10–15K in a moderate scenario.

> Paid LinkedIn is expensive ($10–50 CPM in B2B). It only makes sense for posts that have already shown organic ER >2%. Don't pour budget into average posts.

---

## 9. Risks & Mitigations

| Risk | Likelihood | Impact | Mitigation |
|------|-------------|--------|-----------|
| LinkedIn changes the algorithm | High | Medium | Diversify formats, don't depend on one |
| Carousel fatigue in the niche | Medium | Medium | Text carousels > visual; add video |
| Content creator burnout at 16–20 posts/month | Medium | High | Batch creation (4–5 posts per session) |
| Organic reach keeps declining (industry trend) | High | High | Paid as insurance; newsletter as owned channel |
| Saves aren't growing | Medium | High | A/B test formats; more frameworks and templates |
| Profile-Content Alignment broken | Medium | High | Once a quarter — `/optimize-profile` |

---

## 10. What is NOT included in this template

- **Spec for a specific author** — that's the DIP's job (`Templates/DIP-Template.md`).
- **Topic backlog** — that's the Topic Backlog's job (lives in `Posted/[Author]/Topic-Backlog.md` in your working repo).
- **Tone of voice / banned phrases** — the DIP sections "They NEVER say" and "Speech patterns".
- **Concrete number targets** — fill them in after you've collected your 3-month baseline.
- **Automation tooling** — stats puller, scraper, sync scripts — every team has its own implementation. See `Growth-Loop-Architecture.md` section "File map" for interfaces.

---

## 11. Next steps

1. Fill in your baselines (Section 2).
2. Calibrate `BASE_REACH` and baseline rates from your 3 months of data.
3. Set Q1 targets in Google Sheet.
4. Launch the weekly content cadence from Section 6.
5. After one month — the first monthly review (see `Growth-Loop-Architecture.md` section "Monthly Review").
6. After 3 months — recompute the model coefficients using real correlations.
