# LinkedIn Algorithm Playbook 2026

> Complete guide to the LinkedIn algorithm: how it works, what to do, what to avoid.
> For the team and AI agents. All recommendations are based on data from 8M+ analyzed posts.
> **Last updated:** 2026-03-31
> **Sources:** Richard van der Blom (1.8M posts), Buffer (4.8M posts), AuthoredUp (4.2M posts), Sprout Social (2.7B engagements), LinkedIn Engineering Blog, arXiv papers.

---

## Table of Contents

1. [How the algorithm works](#1-how-the-algorithm-works-360brew)
2. [Post lifecycle](#2-post-lifecycle)
3. [What to write: formats and length](#3-what-to-write-formats-and-length)
4. [What NOT to do](#4-what-not-to-do)
5. [Engagement: likes, comments, shares, saves](#5-engagement-what-works-and-how)
6. [Posting time and frequency](#6-when-and-how-often-to-post)
7. [Profile: how your account should look](#7-profile-how-your-account-should-look)
8. [Consistency and strategy](#8-consistency-and-long-term-strategy)
9. [AI content and automation](#9-ai-content-and-automation)
10. [Personal profiles vs company pages](#10-personal-profiles-vs-company-pages)
11. [Metrics: what to measure, how to calculate, what it affects](#11-metrics-what-to-measure-how-to-calculate-what-it-affects)
12. [Checklists](#12-checklists)

---

## 1. How the algorithm works (360Brew)

### The big picture

In 2025-2026, LinkedIn made a fundamental pivot: **from virality to relevance**. The algorithm now rewards depth, not reach.

**The numbers:**
- Organic reach dropped ~50% for 98% of users
- Median impressions fell from 1,211/post to 636/post (a 47% drop)
- BUT: engagement depth is growing for quality content
- 60% of your reach goes to interest-based clusters (beyond your network)

### 360Brew — LinkedIn's AI engine

In March 2026, LinkedIn launched **360Brew** — a 150-billion-parameter transformer model that completely rebuilt content distribution.

**Two-stage architecture:**

1. **Retrieval (built on LLaMA 3)** — a single model selects candidates for display by generating embeddings for users AND content. Updates in minutes, search in <50ms. Key point: it connects topics even when terminology differs.

2. **Ranking (Generative Recommender)** — processes interaction history as an ordered sequence. Identifies the evolution of interests over time rather than scoring posts in isolation.

### The main shift: semantics instead of signals

| Before | Now (360Brew) |
|--------|-----------------|
| Hashtags, formatting, timing = levers | AI **reads and understands** content like a human |
| Sending "signals" to the algorithm | Quality of thought and depth of expertise |
| Each task = a separate model | One foundation model across 30+ tasks |
| Could be "hacked" | Semantic reasoning, not numeric features |

**Takeaway:** The era of technical tricks is ending. The system understands language, context, and intent. **Quality of thought > hacks.**

### LinkedIn's three official ranking criteria

1. **Relevance** — how precisely the post matches the audience's interests
2. **Expertise** — whether the content demonstrates subject-matter knowledge
3. **Engagement** — whether the post sparks meaningful comments from people interested in the topic

---

## 2. Post lifecycle

### 4 stages

```
STAGE 1: Quality Check (0-60 min)
  └─ Shown to 2-5% of your network. Algorithm evaluates initial engagement.

STAGE 2: Golden Window (0-2 hours) ← CRITICAL, determines 70% of reach
  └─ High engagement → expansion to interest-based clusters
  └─ Low engagement → post "dies"

STAGE 3: Sustained Evaluation (90 min — 8 hours)
  └─ Are comments continuing? Is thread depth growing?

STAGE 4: Extended Distribution (24-48+ hours)
  └─ Quality posts live up to 48 hours and can even be shown
     above fresher ones (confirmed by VP of Product)
```

### What to do in the Golden Window (first 2 hours)

| Action | Effect |
|----------|--------|
| Reply to ALL comments within the first **15 min** | **+90% algorithmic boost** |
| Reply within the first 30 min | +64% total comments, 2.3x views |
| **Do NOT edit the post** | Editing **resets the algorithm** from zero |
| Comment on 5-10 posts in your niche right after publishing | +20% reach, +55% profile views |
| Notify "boosters" in advance | Early engagement from relevant people |
| Reactivate at the 8-hour and 24-hour mark | A comment on your own post triggers re-evaluation |

**Phase 1 (0-90 min):** Post is shown to 2-5% of your network. "Great post!" comments = noise, they don't trigger expansion. Multi-sentence discussions are required.

**Phase 2 (90 min — 8 hours):** If Phase 1 is successful → expansion to interest-based clusters (60% of reach). Evaluated on: are comments continuing? Is discussion depth growing?

---

## 3. What to write: formats and length

### Format ranking by engagement

| # | Format | Engagement Rate | Trend | When to use |
|---|--------|----------------|-------|-------------------|
| 1 | **Carousel (PDF)** | **6.60%** | Consistently high | How-to, frameworks, case studies. Text-based > image-based. **6-9 slides** (not 12+) |
| 2 | **Multi-image** | 6.6% | Stable | Data visualization, comparisons, before/after |
| 3 | **Native Video** | 5.6% | **Reach dropped 35-70%** | Authenticity, behind-the-scenes. <60 sec, vertical, with subtitles |
| 4 | **Text only** | 2-4% | -18% reach | Hot takes, personal stories, deep-dive thought leadership |
| 5 | **Text + Image** | ~3% | Stable | Announcements, insights |
| 6 | **Poll** | ~2% | -35% | Only genuine audience research (not for engagement) |
| 7 | **External links** | ~1% | **~60% penalty** | Only when absolutely necessary |

**Important:** Accounts that **rotate formats** outperform single-format accounts. Don't get stuck on one format.

### Post length

| Length | Result |
|-------|----------|
| <100 words | Good for bold statements and hot takes |
| **1,200-1,800 characters** | **Peak engagement (+47%)** — the sweet spot |
| >1,900 characters | Diminishing returns |
| 3,000 characters (max) | Only if every word is worth its weight in gold |

### The first 210 characters = everything

- Only **210-235 characters** are visible before "See more"
- **60-70% of readers** drop off at the "See more" button
- **360Brew "Lost-in-Distance" Effect:** A vague prologue → algorithmic deprioritization **BEFORE** people scroll through
- The first sentence = semantic anchor for the entire ranking
- Start with a specific problem or pattern, not generic "I wanted to share..."

### What's working now (topics and approaches)

| Pattern | Why it works |
|---------|----------------|
| **Practical frameworks and how-to** | #1 save-worthy content type. Templates, checklists, guides |
| **Build in public** | Behind-the-scenes, real numbers, decisions. Authenticity > polish |
| **Contrarian takes with proof** | Drives comments and debate. Requires data/experience |
| **Original data visualizations** | Stop the scroll, high dwell time |
| **Authentic vulnerability** | 8.5x average engagement. MUST be genuine |
| **Deep-dive text posts** | High dwell time. 360Brew rewards depth |
| **Multi-part series** | Builds anticipation, loyal audience |

### Video: technical requirements

- Duration: <60-90 seconds
- Format: vertical 9:16 (for Video Tab)
- Subtitles: required (most viewers watch without sound)
- Upload: native only (not YouTube links — native = +42% visibility)
- Caption hook: +2.7x watch time
- LinkedIn Live: 24x engagement vs regular video

---

## 4. What NOT to do

### The algorithm penalizes

| What | Consequences | What to do instead |
|-----|-------------|-------------------|
| **Engagement bait** ("Agree?", "Tag someone", "Like if...") | Detected → penalty | Ask genuine on-topic questions |
| **"Link in first comment"** | Penalty (2026) — algorithm detects bridge behavior | Either insert the link after 300+ characters, or skip it |
| **Editing the post** | Resets the algorithm | Proofread BEFORE publishing |
| **2+ posts per day** | **-40%+ reach penalty** on each post | At least 12 hours between posts. Better 24 |
| **Topic-hopping** | Algorithm can't classify your expertise | 2-3 topic clusters max |
| **Profile doesn't match content** | Distribution suppression | Headline and About must match post topics |
| **Engagement pods** | Shadow ban, 60-90 days to recover, up to **-96% reach** | Genuine engagement with real comments |
| **Automated comments** | Removed from "Most Relevant", visibility limited | Only manual, thoughtful comments |
| **Links in the first 300 characters** | Reach reduction | Value upfront, link later |
| **>3 hashtags** | Risk of spam flag. 360Brew doesn't need hashtags | 1-3 relevant ones. Keywords in the text matter more |

### Content mistakes

| What | Why it doesn't work | How to fix |
|-----|-------------------|---------------|
| **Wall of text** | Low readability, high bounce | Short paragraphs (1-3 lines), whitespace, lists |
| **Multiple ideas in one post** | No clear takeaway | ONE idea = one post |
| **"Bro-etry"** (one-line dramatic paragraphs) | Actively suppressed by LinkedIn since mid-2025 | Normal structure. Drama through substance, not formatting |
| **Generic advice without specifics** | Zero differentiation, sounds like AI | Concrete numbers, real examples, personal experience |
| **"I wanted to share..."** | Weak hook. Zero curiosity | Start with a concrete statement |
| **Single image post** | Dead format: -30% vs text | Multi-image or carousel |
| **Generic carousels (style > substance)** | LinkedIn targets low-value carousels | Only with original data/frameworks |
| **Horizontal video** | -80% engagement vs vertical | Vertical 9:16 |
| **YouTube link instead of native upload** | -42% visibility | Always upload natively |

### Tone and style — what kills trust

| What | Why | Use instead |
|-----|--------|-------------|
| **"We/our" in personal posts** | Sounds corporate | Always I/my in personal posts |
| **Overly polished AI text** | -30% reach, -55% engagement | Write in the author's real voice with real examples |
| **Generic motivation** ("In today's world...") | Invisible to the algorithm | A specific observation from real experience |
| **Humble-bragging** ("So humbled...") | Transparent fake modesty | Be direct or don't mention it |
| **"Excited to announce..."** | Tired LinkedIn cliché | Start with the VALUE of the announcement, not the emotion |

---

## 5. Engagement: what works and how

### Signal hierarchy by weight

| Signal | Weight | What it means |
|--------|-----|---------------|
| **Saves** | **Highest** (1 save = 5-10x like) | Strongest signal. Content people come back to |
| **DM Shares/Sends** | Very High | Private shares = powerful signal |
| **Reposts/Shares** | Very High | Especially from influential users |
| **Comments 15+ words** | Very High (2.5x regular) | Thoughtful comments that add context |
| **Thread depth** | High (NEW) | Back-and-forth discussions = strong signal |
| **Dwell Time** | High | **31-60 seconds** = maximum distribution |
| **Comments (any)** | High (2x vs likes) | Velocity in the first 60-120 min is critical |
| **"See more" click** | Medium-High | Interest in long-form content |
| **Profile visits from a post** | Medium | Genuine interest |
| **Likes/Reactions** | **Minimum weight** | The lowest weight of all signals |

**Key takeaway:** 50 comments > 500 likes (3x in reach).

### Saves — the new currency

Saves are the strongest signal. What people save:
- Practical frameworks and templates
- Step-by-step guides
- Checklists
- Reference material

**Tactic:** Add a CTA like "Save this for when you need [X]" for reference content.

### How to comment correctly

**Your own posts (replies):**
- Reply within the first **15 min** (critical)
- Minimum **15 words** (longer = more weight)
- Add value, not just "Thanks!"
- Ask follow-up questions (stimulates the thread)

**Other people's posts:**
- Only in your niche (what you comment on teaches the algorithm)
- Minimum 15 words — a meaty comment
- Add a unique perspective from your experience
- No "Great post!" or "So true!" — these get downranked
- No selling, no pitching

**What NEVER works:**
- "Great post!" — algorithm classifies it as noise, **downrank**
- Comments via automation — removed from "Most Relevant"
- Pod-style identical reactions — detected

### Likes: like or not?

Likes carry **minimal weight** in the algorithm, but:
- Likes from people with relevant job titles → slightly more distribution
- Liking is worth doing — it's baseline engagement, but don't focus on it
- **Comments matter far more than likes** — one good comment > dozens of likes

### Share or not?

- **Repost with a comment** — strong signal, especially from influential users
- **Repost without a comment** — treated as low-effort
- **DM share** — one of the strongest signals (private shares)
- Sharing is worth doing, but **with an original comment**, not just a repost

---

## 6. When and how often to post

### How to systematically identify the best time

**Principle:** Best time = when the maximum of your target audience is on LinkedIn + factoring in the 48-hour post lifespan.

**Step 1: Identify the audience's timezone**
- Where are your readers geographically?
- Are there "boosters" in other timezones?

**Step 2: Pick the day with lifespan in mind**

Thanks to the 48-hour lifespan, choose a day so that the post's **"tail"** lands on strong days:

| Publication day | Post "tail" covers | Rating |
|----------------|------------------------|--------|
| **Tuesday** | Wednesday + Thursday | **Ideal** |
| **Wednesday** | Thursday + Friday | Good |
| **Monday** | Tuesday + Wednesday | Good |
| **Thursday** | Friday + Saturday | Worse |
| **Friday** | Saturday + Sunday | Bad |

**Step 3: Pick the time**

| Slot | When it fits | Comment |
|------|---------------|-------------|
| **Morning (9-10 AM EST)** | Audience in the US + Europe | European boosters can drive early engagement |
| **Evening (3-5 PM EST)** | US audience only | New trend (Buffer, 4.8M posts), but Europe is already offline |

**Step 4: Analyze your own analytics**
- Look at your own data in LinkedIn Analytics
- Test different slots over 4-6 weeks
- Track: impressions, engagement rate, comment velocity in the first hour

### Day ranking

| Day | Rating | Comment |
|------|---------|-------------|
| **Tuesday** | #1 (tied) | Consistently peak day for B2B |
| **Wednesday** | #1 (tied) | Buffer (4.8M posts) — #1 day |
| **Thursday** | #2 | All sources agree |
| **Monday** | #3 | Lifespan covers Tuesday-Wednesday |
| **Friday** | #4 | Only until 2 PM. Lifespan rolls into the weekend |
| **Weekend** | Avoid | Engagement drops 40-60% |

### Posting frequency

| Frequency | Effect |
|---------|--------|
| 1 post/week | Minimum. Almost no algorithmic momentum |
| **2-3/week (for executives)** | **Best ROI** on lead generation |
| **3-5/week** | **Sweet spot** for creators and growth |
| 5-7/week | Works IF quality is consistent and 1 post/day |
| **2+ posts/day** | **PENALTY: -40%+ reach on each post** |

**Critically important:** The "post every day" approach is **dead** if it means sacrificing quality. One well-researched post with 2 min dwell time >> 5 short superficial posts.

### Anti-Cannibalization rule

- Minimum **12 hours** between posts from the same author
- Between posts from different authors on the same topic: **2-3 days**
- Don't post on Friday after 2 PM — loses momentum over the weekend
- **No more than 1 post per day** — real penalty for 2+/day

---

## 7. Profile: how your account should look

### Why the profile = 50% of success

360Brew **cross-checks** posts against the profile (Headline, About, Experience). Semantic mismatch between content and profile → **distribution suppression**.

### Headline (220 chars max, first 60 visible in the feed)

**Formula:** `[Role/Identity] | [Core Expertise 1] + [Core Expertise 2] | [Unique Differentiator]`

**Rules:**
- Keywords from post topics MUST be in the headline (Profile-Content Alignment)
- First 60 chars = what people see in the feed and comments → put the most important content here
- Avoid: "Thought Leader", "Visionary", "Guru", "Passionate" — buzzwords without substance
- Update when content focus shifts

### About / Summary (5 paragraphs)

```
1. HOOK — Who you are and why it matters (2-3 sentences)
   NOT "I am a passionate..." → "I've spent 20 years building..."

2. STORY — Key turning point / transformation
   "After building X, I realized Y. That's why I'm now doing Z."

3. WHAT I DO NOW — Current focus with specifics

4. PROOF — Numbers, case studies, social proof

5. CTA — What to do next
   "DM me if [specific reason]. I share [topic] here weekly."
```

**Rules:**
- Write in the **first person** (I/my)
- Industry keywords naturally in the text (for 360Brew and search)
- Over 40 words — otherwise it isn't indexed in search
- Update every 3-6 months

### Photo and banner

- **Photo:** Professional, friendly, recent. Face = 60%+ of the frame. No pets, no family
- **Banner:** Branded, clean design with a tagline or value prop
- Profiles with a photo → **3x connection requests**, **2x profile views**

### Experience

- Current Role **MUST be filled in** (empty = semantic gap for 360Brew)
- Description: achievements > responsibilities
- Numbers and results > generic descriptions

### Skills & Endorsements

- **5+ skills** → **2.9x profile views**, **4.7x messages**
- Top 3 skills are shown first — choose strategically
- Endorsements from connections → boost credibility

### Verifications

- Verified profiles → **60% more profile views**
- Identity verification via government ID
- Workplace verification via work email
- Free

### Featured Section

- Best posts from the last quarter
- PDF frameworks, checklists
- Links to your site, lead magnet
- Update once a quarter

### Creator Mode

- Activate for: amplified content, Featured higher up, Newsletter access
- Up to 5 profile topics (tags)
- Follow link instead of Connect

---

## 8. Consistency and long-term strategy

### The 90-day semantic authority cycle

360Brew builds your **"topic DNA"** over ~90 days of consistent posting. This means:

- **3-4 topic clusters max** — don't jump between topics
- **90 days** is needed to form semantic categorization
- After that, 60% of reach goes to interest-based clusters (beyond your network)
- Network size matters less than **semantic depth of content**

### Niche depth > Network size

360Brew uses **zero-shot reasoning** to match niche authors with relevant audiences. This means:

- Niche expertise = advantage, not limitation
- Educational posts with frameworks and data = amplification beyond your network
- Follower count shortcuts no longer work
- New users gain the most (the LLM matches interests semantically)

### Consistency rules

| Metric | Recommendation |
|---------|-------------|
| Minimum posts | 1/week (baseline) |
| 2+ week break | Algorithmic momentum dies |
| Topic clusters | 2-4 max, stick to them |
| Profile-Content alignment | Update headline when topics shift |
| Quarterly audit | Review your profile every 90 days |

### The formula for sustainable growth

```
Consistent niche posting (3-5/week)
  + Profile aligned with content
  + Thoughtful comments in your niche (daily)
  + Save-worthy content (frameworks, guides)
  + Genuine engagement (no pods, no automation)
  = Sustainable organic growth under 360Brew
```

---

## 9. AI content and automation

### AI content: detected and penalized

| Signal | Impact |
|--------|---------|
| AI-generated content detected | **-30% reach, -55% engagement** |
| Repetitive wording, overly polished tone | Triggers detection |
| AI comments (timing, language patterns) | Under monitoring |
| EU mandatory AI labeling | From August 2, 2026 |

**Best practice:** AI for research and drafting → rewrite in an authentic voice with personal examples. Don't publish raw AI output.

### Pods and automation = dead

LinkedIn VP of Product: the goal is to make engagement pods **"entirely ineffective"**.

- **Lempod** (the most popular one) — banned, removed from the Chrome Web Store
- **Coordinated Activity Rings** — LinkedIn maps clusters of accounts reacting to each other
- **Shadow bans** — recovery: 60-90 days. Case study: reach dropped from 8,500 to 340 impressions (-96%)
- **Automated comments** — removed from "Most Relevant", visibility limited

**Coordinating with colleagues = OK**, as long as it's genuine engagement (thoughtful comments, at different times, no templates).

---

## 10. Personal profiles vs company pages

| Metric | Personal profile | Company page |
|---------|---------------|----------------------|
| Share in the feed | **65%** | **5%** |
| Organic reach | ~8-12% of followers | **~1.6%** of followers |
| Reach comparison | **561% more** (same content) | Baseline |
| Impressions | **2.75x more** | Baseline |
| Engagement | **5x more** | Baseline |

**CEO/Founder content** = 4x average engagement.
**Employee advocacy** = **7x better leads** vs the company page.

**Strategy:** Personal profiles = primary distribution. Company page = content hub + secondary amplification.

---

## 11. Metrics: what to measure, how to calculate, what it affects

### Metrics map: what affects what

```
PROFILE STRENGTH (Headline + About + Skills + Verifications)
  │
  ▼
CONTENT QUALITY (hook + depth + format + topic alignment)
  │
  ├──→ Impressions (how many people saw the post)
  │       │
  │       ▼
  ├──→ Engagement (actions on the post)
  │       │
  │       ├──→ Saves, Comments, Shares → Algorithmic Boost → more Impressions
  │       │
  │       ├──→ Profile Visits → Followers
  │       │
  │       └──→ DM Conversations → Leads / Opportunities
  │
  └──→ Follower Growth (long-term asset)
          │
          ▼
        Base Audience → higher initial reach for future posts
```

**Key chain:** Content Quality → Engagement → Impressions → Profile Visits → Followers → larger Base Reach → more Impressions. A flywheel.

### Formulas for calculating key metrics

#### 1. Engagement Rate (ER) — the main content quality metric

```
ER = (Likes + Comments + Shares + Saves) / Impressions × 100%
```

| Value | Rating |
|----------|--------|
| <2% | Below average — revisit the hook, topic, or format |
| 2-4% | Average level for text-only posts |
| 4-6% | Good result |
| 6%+ | Excellent — carousel and multi-image territory |
| 10%+ | Viral — analyze and repeat the pattern |

**Benchmarks by format:**

| Format | Average ER | Source |
|--------|-----------|---------|
| Carousel (PDF) | 6.60% | SocialInsider 2025 |
| Multi-image | 6.60% | SocialInsider 2025 |
| Native Video | 5.60% | SocialInsider 2025 |
| Text only | 2-4% | Multiple sources |
| Text + Image | ~3% | Multiple sources |
| Poll | ~2% | van der Blom 2025 |
| External links | ~1% | Practitioner consensus |

#### 2. Weighted Engagement Score (WES) — the real value of engagement

Not all actions are equal. Formula factoring in algorithmic weights:

```
WES = (Saves × 8) + (DM Shares × 5) + (Reposts × 4) + (Comments 15+ words × 2.5)
    + (Comments any × 2) + (Likes × 1)
```

**Why:** Two posts can have the same ER, but a post with 10 saves and 5 deep comments will have a WES = 92.5, while a post with 50 likes and 2 "Great post!" comments = 54. The first one will get many times more distribution.

**How to use:** Calculate WES for each post. Compare WES/Impression — this shows the real quality of engagement, not just quantity.

```
WES per 1K Impressions = WES / (Impressions / 1000)
```

| WES/1K Impressions | Rating |
|--------------------|--------|
| <5 | Low engagement quality |
| 5-15 | Average level |
| 15-30 | Good quality engagement |
| 30+ | Excellent — content generates saves and deep comments |

#### 3. Save Rate — the metric for save-worthy content

```
Save Rate = Saves / Impressions × 100%
```

| Value | Rating |
|----------|--------|
| <0.5% | Content isn't save-worthy — add actionable frameworks |
| 0.5-1% | Average level |
| 1-2% | Good — content has reference value |
| 2%+ | Excellent — people keep it as a reference |

**Why it matters more than ER:** 1 save = 5-10x a like in the algorithm. A post with a 1% save rate and 2% ER will get better distribution than a post with a 0.1% save rate and 5% ER.

#### 4. Comment Depth Ratio — discussion quality

```
Comment Depth Ratio = Reply Comments / Total Comments × 100%
```

| Value | Rating |
|----------|--------|
| <20% | People comment, but the author/audience don't reply |
| 20-40% | Normal discussion level |
| 40-60% | Active discussion — strong algorithmic signal |
| 60%+ | Deep discussion — top-tier for 360Brew |

**Why:** Thread depth is a new high-weight signal in 360Brew. Back-and-forth discussions weigh more than isolated comments.

#### 5. Dwell Time Proxy — indirect estimate

LinkedIn doesn't show dwell time directly, but you can estimate it:

```
Dwell Time Proxy = (Impressions with a "See more" click) / Total Impressions
```

If the post is long (1,200+ chars) and the "See more" click rate is high — it means people are reading.

**Optimum:** 31-60 seconds dwell time = maximum distribution. Case study: a post with 8 comments but average dwell time of 4 minutes → 45,000 reach.

#### 6. Follower Conversion Rate — how well content converts into followers

```
Follower Conversion = New Followers (over period) / Total Impressions (over period) × 100%
```

| Value | Rating |
|----------|--------|
| <0.1% | Content doesn't motivate people to follow — revisit profile alignment |
| 0.1-0.3% | Normal level |
| 0.3-0.5% | Good — content + profile work in sync |
| 0.5%+ | Excellent — strong authority signal |

**What drives it:** Profile-Content Alignment is critical. If the post is about AI agents and the headline says "Marketing Manager" — conversion will be low.

#### 7. Velocity Metrics — speed of engagement accumulation (Golden Window)

```
Comment Velocity = Comments in the first 60 min / Total Comments × 100%
Engagement Velocity = Total Engagement in the first 2 hours / Total Engagement × 100%
```

| Comment Velocity | Rating |
|-----------------|--------|
| <30% | Slow start — weak Golden Window |
| 30-50% | Normal |
| 50-70% | Good — boosters are working |
| 70%+ | Excellent — post "took off" from the first minutes |

**Why:** If >70% of engagement comes in the first 2 hours and then silence — the post didn't get extended distribution. If engagement keeps growing after 8 hours — the post entered Stage 4.

### What to measure for reporting

#### Weekly report (per author)

| Metric | Where to get it | Why |
|---------|-------------|-------|
| Posts published | Count | Posting frequency (target: 2-5/week) |
| Total Impressions | LinkedIn Analytics | Reach volume |
| Avg ER per post | Calculate via formula | Content quality |
| Total Saves | LinkedIn Analytics | Save-worthy score |
| Avg WES per post | Calculate via formula | Real quality engagement |
| New Followers | LinkedIn Analytics | Audience growth |
| Profile Views | LinkedIn Analytics | Interest in the author |
| Top post (by WES) | Calculate | What worked best |

#### Monthly report (cross-author)

| Metric | Formula | Why |
|---------|---------|-------|
| Impressions trend | MoM % change | Is reach growing? |
| ER trend | MoM change | Is quality growing? |
| Save Rate trend | MoM change | Is save-worthy content growing? |
| Follower Growth Rate | New Followers / Starting Followers × 100% | Audience growth rate |
| WES per 1K Impressions trend | MoM change | Is quality of engagement improving? |
| Best format (by WES) | Compare across formats | Which format works better |
| Best topic cluster (by ER) | Compare across clusters | Which topic resonates |
| Comment Depth Ratio trend | MoM change | Are discussions getting deeper? |

#### Quarterly audit (strategic)

| Question | How to answer | Action |
|--------|-------------|----------|
| Is reach growing? | Impressions MoM over 3 months | If declining → revisit topics / profile |
| Is quality growing? | WES/1K Impressions trend | If declining → more save-worthy content |
| Are we converting into followers? | Follower Conversion Rate | If low → Profile-Content Alignment audit |
| Which format is best? | ER and WES by format over the quarter | Increase share of the best, test new ones |
| Which topic resonates? | ER by topic cluster | Go deeper on strong ones, revisit weak ones |
| Is follower "weight" growing? | Comments from relevant job titles | If not growing → revisit targeting |

### How followers affect reach (and vice versa)

```
Followers → Base Audience (2-5% see the post in Stage 1)
  │
  ├─ 1,000 followers → 20-50 people see the post initially
  ├─ 5,000 followers → 100-250 people see the post initially
  ├─ 10,000 followers → 200-500 people see the post initially
  │
  └─ BUT: 60% of total reach goes to interest-based clusters (OUTSIDE followers)
     → For 360Brew, content quality > follower count
```

**Practical math:**
- Organic reach: ~8-12% of followers for personal profiles, ~1.6% for company pages
- Median impressions/post: 636 (2025 data, AuthoredUp)
- BUT: quality content with high WES can get 10-50x the median

**Takeaway:** Followers are starter fuel, not the end goal. 1,000 engaged followers who give saves and deep comments > 10,000 passive followers who only give likes. Focus on WES, not follower count.

### Dashboard Template

For each author, collect this data weekly:

```
| Week | Posts | Impressions | Avg ER | Total Saves | Save Rate | WES Total | WES/1K Imp | New Followers | Profile Views | Best Post (hook) |
|--------|-------|-------------|--------|-------------|-----------|-----------|------------|---------------|---------------|------------------|
| W1     |       |             |        |             |           |           |            |               |               |                  |
| W2     |       |             |        |             |           |           |            |               |               |                  |
| W3     |       |             |        |             |           |           |            |               |               |                  |
| W4     |       |             |        |             |           |           |            |               |               |                  |
| MONTH  |       |             |        |             |           |           |            |               |               |                  |
```

### Decision Framework: when to change strategy

| Signal | What it means | What to do |
|--------|-----------|------------|
| ER falling, Impressions stable | Content has become less engaging | Revisit hooks, format, or topics have "worn out" |
| Impressions falling, ER stable | Algorithm has narrowed distribution | Check Profile-Content Alignment, increase comment activity |
| Saves falling, Likes rising | Content entertains but isn't save-worthy | Add frameworks, checklists, actionable guides |
| Followers growing, ER falling | Audience is expanding beyond the niche | Narrow topics, return to core expertise |
| Comment Depth falling | People aren't holding discussions | Ask concrete questions, seed first comments |
| WES/1K rising while Impressions fall | Content is strong but reach is limited | Increase frequency to 3-5/week, comment more actively in the niche |
| Profile Views rising, Followers not | People look at the profile but don't follow | **Profile audit:** headline, about, featured section |

---

## 12. Checklists

### Before publishing a post

- [ ] Day: Tuesday-Wednesday (ideal), Monday-Thursday (good)
- [ ] Time: optimal for your audience's timezone
- [ ] Hook within the first 210 characters — specific, intriguing
- [ ] No engagement bait (no "Agree?", "Tag someone")
- [ ] No "bro-etry" (one-line dramatic paragraphs)
- [ ] No AI-sounding generic text
- [ ] First person (I/my), not "we/our" in a personal post
- [ ] Not a single image post
- [ ] Length 1,200-1,800 characters (sweet spot) or justifiably shorter/longer
- [ ] Topic matches the profile headline
- [ ] Concrete examples / numbers / stories
- [ ] CTA is specific, not generic
- [ ] 1-3 hashtags max (or zero)
- [ ] No links (or link after 300+ characters of value)
- [ ] At least 12 hours since the last post
- [ ] No more than 1 post per day
- [ ] Boosters notified

### After publishing (Golden Window)

- [ ] Reply to ALL comments within the first 15 minutes
- [ ] Do NOT edit the post
- [ ] Comment on 5-10 posts in your niche
- [ ] Reactivate: comment on your own post at the 8-hour mark
- [ ] Reactivate: at the 24-hour mark

### Quarterly profile audit (every 90 days)

- [ ] Does the headline contain 2-3 key post topics?
- [ ] Does the About section tell a story rather than list skills?
- [ ] Is the Current Role filled in?
- [ ] Featured section — best posts of the quarter?
- [ ] 5+ current skills? Top 3 strategically chosen?
- [ ] 3+ fresh recommendations?
- [ ] Banner up to date?
- [ ] Do post topics over the past 90 days match Headline + About?
- [ ] Verifications connected?
- [ ] Creator Mode activated?

---

## Sources

### Primary Research (raw data)
- **Richard van der Blom** — Algorithm InSights Report 2025 (1.8M posts, 58K profiles, 31K company pages)
- **AuthoredUp** — 621,000+ posts tracked + 4.2M posts timing analysis
- **Buffer** — 4.8M posts timing + 2M+ posts strategy analysis
- **SocialInsider** — LinkedIn Benchmarks 2025
- **Sprout Social** — 2.7B engagements analyzed
- **Postiv AI** — 2M+ LinkedIn posts analysis

### Algorithm Architecture
- LinkedIn Engineering Blog: "Large Scale Retrieval for the LinkedIn Feed" (Hristo Danchev, March 12, 2026)
- arXiv: "Large Scale Retrieval for the LinkedIn Feed using Causal Language Models" (arXiv:2510.14223)
- Search Engine Land: "LinkedIn updates feed algorithm with LLM-powered ranking and retrieval"

### Expert Practitioners
- Jasmin Alic: 26 Essential LinkedIn Tips 2026
- Matt Navarra: How LinkedIn Algorithm Works 2025
- Rock Your LinkedIn Profile course: Rock Your LinkedIn Profile
- How to Build a Strong Brand course: How to Build a Strong Professional Brand
- Marketing on LinkedIn course: Marketing on LinkedIn
- Profile Nano Tips course: Optimizing Your LinkedIn Profile Nano Tips

### LinkedIn Official
- LinkedIn VP of Product: Engagement pods goal, old posts display, 3 ranking criteria
- LinkedIn Sr. Director of Product: Link penalty nuance
- LinkedIn Engineering Blog: Dwell Time, 360Brew architecture

---

*Last updated: 2026-03-31. Update monthly as new data about the algorithm appears.*
