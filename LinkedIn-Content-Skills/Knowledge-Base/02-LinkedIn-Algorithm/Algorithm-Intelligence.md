# LinkedIn Algorithm Intelligence — 2026

> Living reference: current information on the LinkedIn algorithm for post optimization.
> **Last updated:** 2026-03-17
> **Data sources:** Richard van der Blom Algorithm InSights 2025 (1.8M posts), Buffer (2M+ posts), SocialInsider, Hootsuite, Sprout Social, Jasmin Alic, LinkedIn Engineering Blog (March 2026), Search Engine Land, pettauer.net, AuthoredUp (621K+ posts).

---

## 1. THE BIG PICTURE: Precision > Broadcast

In 2025-2026 LinkedIn made a fundamental pivot: from virality to relevance. The algorithm now rewards **depth**, not **reach**.

**Key numbers (Richard van der Blom, 1.8M posts analyzed):**
- Organic reach dropped **~50%** for 98% of users
- Engagement declined **~25%** on average across the platform
- Follower growth slowed by **59%** YoY
- BUT: engagement depth is growing for quality content

**AuthoredUp (621K+ posts):** Median impressions dropped from **1,211/post** (June 2024) to **636/post** (May 2025) — a **47%** decline. 98% of users affected.

**What this means for us:**
- Volume of posts does NOT compensate for quality
- Niche authority matters more than frequency
- Posts live up to **48 hours** (previously a few hours) if they generate discussion
- LinkedIn confirmed: surfacing older posts above new ones is an **intentional** decision (VP of Product, mid-June 2025)
- Evergreen content with practical value = long tail
- **60% of your reach goes to interest-based clusters** (outside your network) — 360Brew redistributes audience

---

## 2. 360BREW: LINKEDIN'S AI ALGORITHM (MAJOR UPDATE March 2026)

### What 360Brew is

LinkedIn launched **360Brew** — a **150-billion-parameter decoder-only transformer foundation model** that fully rebuilt content distribution. It handles **30+ predictive tasks** simultaneously: Feed, Job Recommendations, Search, Ads. Previously these tasks were served by separate models.

> **Source:** LinkedIn Engineering Blog, March 12, 2026 (Hristo Danchev); arXiv paper "Large Scale Retrieval for the LinkedIn Feed using Causal Language Models"

### Two-stage LLM architecture (NEW)

**Stage 1 — Unified Retrieval System (LLaMA 3 fine-tune):**
- Previously, feed candidates came from several separate systems (network activity, trending, collaborative filtering, topic-based)
- Now — a single LLM-based model built on **Meta LLaMA 3**
- Uses a **dual-encoder architecture**: generates embeddings for users AND content from text input
- Content embeddings refresh **within minutes**; candidates are retrieved **in <50 milliseconds**
- Key capability: **links topics even when terminology differs** (engagement with "small modular reactors" → exposure to content about "electrical grid infrastructure")

**Stage 2 — Transformer-Based Generative Recommender (GR) Ranking:**
- Uses **causal attention** — a user's interaction history is processed as an **ordered sequence**
- Posts are scored chronologically alongside actions (likes, comments, dwell time)
- Captures the **evolution of professional interests** over time, rather than scoring posts in isolation
- Runs on **GPU clusters (H100s)** at scale

### The main shift: from signals to semantic reasoning

| Old algorithm | 360Brew (2026) |
|-----------------|----------------|
| Sum of weighted numeric features | Probabilistic semantic reasoning |
| Hashtags, formatting, timing = levers | Understanding of language, context, intent |
| Signals can be "hacked" | AI reads content like a human |
| Separate models for different tasks | One foundation model across 30+ tasks |
| Numerical vectors | Natural language prompts (In-Context Learning) |

**Practical meaning:** The era of "sending signals" (hashtags, formatting, timing tricks) is ending. The system **understands language, context, and reasoning**. Quality of thought > technical tricks.

### 8 key factors (updated)

| # | Factor | What it means | What to do |
|---|--------|---------------|-----------|
| 1 | **Profile-Content Alignment** | The algorithm cross-checks posts against Headline, About, Experience. Semantic divergence → distribution suppression | Headline and About must match post topics. Current Role field is required (empty → semantic gap) |
| 2 | **Topic Consistency** | ~90 days of consistent posting are needed for semantic categorization. 3-4 topical pillars max | Don't jump between topics. The clusters from the DIP are your guide |
| 3 | **First Sentence = Anchor** | The first line gets **disproportionate attention weighting** from the algorithm. "Lost-in-distance" effect: a vague prologue = deprioritization BEFORE people scroll | Open with a concrete problem or pattern, not a generic line |
| 4 | **Saves > Likes** | 1 save = **5-10x** the weight of a like. A post with 200 saves dramatically outperforms one with 1,000 likes | Create save-worthy content: frameworks, guides, templates |
| 5 | **Comments Train Profile** | What you comment on trains the model. Comments from people **in your industry** carry more weight | Thoughtful comments of 15+ words in your niche |
| 6 | **Links = Heavy Penalty** | Links bring a **~60% reduction in reach**. "Link in first comment" is also penalized (2026) | Avoid links where possible. If needed — value first, link after ~300 characters |
| 7 | **Structure Helps AI** | 360Brew reads text semantically. Clear paragraphs improve parsing and distribution | Short paragraphs, lists, whitespace. Natural industry keywords in the text |
| 8 | **Hashtags = Minimal** | 360Brew understands context directly from text. Hashtags are **significantly deprioritized** | **1-3** (was 3-5). Relevant keywords in the text itself matter more than hashtags. More than 3 → risk of a spam flag |

---

## 3. CONTENT LIFECYCLE (4 stages)

```
STAGE 1: Quality Check (0-60 min)
  └─ Shown to 2-5% of your network. The algorithm evaluates initial engagement.

STAGE 2: Golden Window (0-2 hours) ← CRITICAL, determines 70% of reach
  └─ If engagement is high → expansion to interest-based clusters (60% of reach)
  └─ If low → the post "dies"

STAGE 3: 8-Hour Review
  └─ Sustained engagement assessment. Are comments still coming in?

STAGE 4: Extended Distribution (24-48 hours)
  └─ Decision on broader distribution. Can live up to 48+ hours.
  └─ LinkedIn intentionally surfaces quality week-old posts above new ones.
```

### What to do in the Golden Window (first 2 hours)

| Action | Effect |
|----------|--------|
| Reply to ALL comments in the first 30 min | +64% total comments, 2.3x views |
| Reply within the first 15 min | +90% algorithmic boost |
| Do NOT edit the post | Editing resets the algorithm |
| Comment on 5-10 posts in your niche right after | +20% reach, +55% profile views |
| Notify "boosters" in advance | Early engagement from relevant people |

---

## 4. ENGAGEMENT SIGNALS (hierarchy by weight — updated March 2026)

| Signal | Weight | What it means |
|--------|-----|---------------|
| **Saves** | Highest (1 save = **5-10x** a like) | The strongest signal. Content people return to |
| **DM Shares/Sends** | Very High | Private shares = strong signal. Appeared in analytics in late 2025 |
| **Reposts/Shares** | Very High | Especially from influential users |
| **Comments 15+ words** | Very High (2.5x regular comments) | Thoughtful comments that add context. **50 comments > 500 likes** in reach (3x) |
| **Comment Thread Depth** | High (NEW) | Replies to comments weigh **higher** than isolated comments. Back-and-forth discussions = strong signal |
| **Dwell Time** | High | **31-60 seconds** = maximum distribution. Case: 8 comments, avg 4 min dwell → 45,000 reach |
| **Comments (any)** | High (2x vs likes) | Velocity in the first 60-120 min is critical |
| **Click-through ("See more")** | Medium-High | Interest in longer content |
| **Profile visits from post** | Medium | Content sparked genuine interest |
| **Reactions (likes)** | Baseline (minimal weight) | Still counted, but **the lowest weight** of all signals |

### The Save Economy

Saves are the NEW CURRENCY. Content that people save: practical frameworks, templates, step-by-step guides, reference material. This outperforms content built for likes.

**Implications:**
- Add a "Save this" CTA for reference content
- Frameworks and checklists = high save rate
- Carousels with actionable steps = save machines

### "Great post!" = noise

- **"Great post!"** comments and low-entropy engagement = noise, **downranked** (NEW)
- The algorithm evaluates **lexical diversity** and conversational depth
- Comments from people with **relevant job titles** → more distribution

---

## 5. ENGAGEMENT PODS & AUTOMATION CRACKDOWN (NEW — 2026)

### Pods are dead

LinkedIn VP of Product: the goal is to make engagement pods **"entirely ineffective."**

| Measure | Details |
|------|--------|
| **Lempod** (the most popular) | Banned, removed from the Chrome Web Store |
| **Browser-based comments** | Comments via third-party scripts/plugins are **removed from "Most Relevant"** (February 2026) |
| **Coordinated Activity Rings** | LinkedIn maps clusters of accounts that react to each other's posts in the first minutes |
| **Shadow bans** | Recovery period: **60-90 days**. One marketing director: reach dropped from 8,500 to 340 impressions = **-96%** |

### Automated comments

LinkedIn: "We may limit the visibility of comments... if we detect excessive comment creation or use of an automation tool."

- Patterns: timing, language patterns, repetitive structure → flagging
- Lexical diversity = one of the signals separating genuine from automated activity

### What to do about it

- **No pod tools.** Even "harmless" ones — the algorithm sees the patterns
- Coordination with "boosters" = OK, if it's genuine engagement (thoughtful comments, at different times)
- Comment quality > the speed of a group's reaction

---

## 6. FORMAT PERFORMANCE (ranked by engagement — updated March 2026)

| # | Format | Engagement Rate | Reach Trend | Best For | Notes |
|---|--------|----------------|-------------|----------|-------|
| 1 | **Carousel/Document (PDF)** | **6.60%** | Stable-High | How-to, frameworks, case studies | Best format. ~6x engagement vs text. Up to 11x impressions. **Text-oriented > image-oriented**. Optimum is **6-9 slides** (was 12-13 — carousel fatigue) |
| 2 | **Video (native, short)** | 5.6% | **DOWN 35% reach** | Behind-scenes, tips, demos | IMPORTANT: native video reach **dropped 35%** (van der Blom). Per 360Brew data — **up to 70% decline**. Text-first indexing bias. <90 sec, vertical, captions. Still good for authenticity |
| 3 | **Multi-image** | 6.6% | Stable | Data visualizations, comparisons | Underrated format |
| 4 | **Text only** | 2-4% | Down 18% | Hot takes, personal stories | Dwell time saves good text. Drives more substantive comments. Ideal for thought leadership |
| 5 | **Text + Image** | ~3% | Stable | Announcements, insights | Single image underperforms text by 30% — reversal from 2024 |
| 6 | **Poll** | ~2% | Down 35% | Audience research (rare) | Multiplier from 1.64x to 1.19x. 3 options + 7 days best. Polls with thoughtful commentary still work |
| 7 | **External links** | ~1% | Heavy penalty | Only when necessary | **~60% reach reduction**. The heaviest penalty of all content factors. "Link in first comment" is also penalized |

### Video Specs That Work

- **Duration:** <90 seconds (highest engagement), ideally <60 sec
- **Format:** Vertical 9:16 (for Video Tab)
- **Captions:** Always (most consumption = sound-off)
- **Upload:** Native only (not YouTube links — native = +42% visibility)
- **Hook in caption:** +2.7x watch time
- **LinkedIn Live:** 24x more engagement vs standard video
- **Caveat (2026):** Reach crashed. Use video for authenticity/personal connection, but don't expect carousel-level reach

### Format Rotation

Accounts that **rotate formats** (carousel + video + text + polls) outperform single-format accounts. Don't get stuck on one format.

---

## 7. POST LENGTH

| Length | Performance | Best For |
|--------|------------|----------|
| **<100 words** | High for quick hits | Bold statements, hot takes, questions |
| **1,200-1,800 characters** | **PEAK (+47% engagement)** | Complete narratives, frameworks |
| **1,300-1,900 characters** | Peak zone (10K+ post analysis) | Sweet spot: full narrative in a 60-90 sec read |
| **>1,900 characters** | Diminishing returns | Only for deeply valuable content |
| **3,000 characters (max)** | Only if every word earns its place | Long-form thought leadership |

### First 210 Characters = Everything

- Only the first **210-235 characters** are visible before "See more"
- **60-70%** of potential readers are lost at "See more"
- The hook MUST live here. This is the most valuable real estate in the post.
- **360Brew "Lost-in-Distance" Effect:** vague or generic prologues → deprioritization **BEFORE** people scroll. The first sentence = the anchor for all algorithmic ranking.

---

## 8. TIMING & FREQUENCY (updated)

### Best Days and Times

| Day | Best Time | Notes |
|-----|-----------|-------|
| **Tuesday** | 10:00 AM local | #1 — consistently highest engagement |
| **Wednesday** | 10:00 AM or 3:00 PM | Strong performer |
| **Thursday** | 10:00 AM | #2 overall |
| **Monday** | 8:00-9:00 AM | Good for week-opening content |
| **Friday** | Lower | Lighter/personal content only |
| **Weekend** | Avoid | Lowest engagement (-45%) |

**For our team** (USA audience, LA founder, EU boosters):
- **6-7 AM LA / 15-16:00 CET** — ideal: US peak + Europeans at work
- EU boosters provide early engagement → US sees the post with momentum

### Frequency (UPDATED)

| Frequency | Effect |
|-----------|--------|
| 1 post/week | Baseline — minimal algorithmic momentum |
| **3-5 posts/week** | **Sweet spot** — optimal quality/reach balance |
| **2/week (for executives)** | Often the best lead-gen ROI |
| **2+ posts/day** | **PENALTY: -40%+ reach per post** |
| 11+/week | Only for full-time creators. Hurts most people |

**CRITICAL:** The "post every day" approach is **dead**. One well-researched post with 2 min dwell time = significantly more than 5 short superficial posts. **Quality > frequency** — this is no longer advice, it's the algorithm's mechanics.

### Anti-Cannibalization

- Minimum **12 hours** between posts from the same author
- Between posts from different authors on the same topic: **2-3 days**
- Don't post on Friday after 14:00 — loses momentum over the weekend

---

## 9. SUGGESTED POSTS & BEYOND-NETWORK DISTRIBUTION (NEW)

### How distribution works in 2026

The algorithm determines your **"topic DNA"** and distributes content based on demonstrated expertise, not network size.

**Distribution order:**
1. **First:** Active relationship clusters (1st-degree connections that engage with you)
2. **Then:** Interest-based clusters (**60% reach** goes here under 360Brew)
3. **Expansion:** If the content performs → non-connected users with interest in the topic

**Zero-shot reasoning** in 360Brew allows niche authors to be matched with relevant audiences quickly based on **semantic depth** rather than historical engagement.

**New users benefit the most:** A/B tests showed significant engagement gains among new users — the LLM matches their interests semantically instead of using the network graph.

**Interest Picker:** LinkedIn added a feature at signup for fast feed personalization.

### What this means for our strategy

- Network size matters less than **semantic depth of content**
- Niche expertise (AI agents for performance marketing) = an advantage, not a limitation
- Educational posts with frameworks and data = amplification beyond your network
- Follower-count shortcuts no longer work

---

## 10. WHAT'S WORKING NOW (March 2026)

| Pattern | Why It Works | Shelf Life |
|---------|-------------|------------|
| **Practical frameworks & how-tos** | #1 save-worthy content type. Templates, checklists, guides | Evergreen |
| **"Build in public" content** | Behind-the-scenes authenticity. Growing trend | 6+ months |
| **Contrarian takes with evidence** | Drives comments, debate. Data/experience backing critical | Ongoing |
| **Data visuals (original data)** | Stops scroll, high dwell time | Ongoing |
| **Vulnerable/authentic stories** | 8.5x average engagement. Must be genuine | Ongoing if genuine |
| **Industry insights + original analysis** | Not just reporting news, but adding interpretation | Ongoing |
| **Short-form native video** | <90 sec, vertical. Reach is down, but authenticity value is high | Stable (lower reach) |
| **Multi-part series** | Builds anticipation, loyal audience | 3-6 months |
| **Deep-dive text posts** | High dwell time. 360Brew rewards depth over format | Rising |

---

## 11. WHAT'S DECLINING / DEAD

| Pattern | Status | Detail |
|---------|--------|--------|
| **"Bro-etry"** | Actively suppressed | Single-line dramatic paragraphs — LinkedIn penalizes |
| **Engagement bait** | Penalized | "Agree?", "Tag someone", "Like if you..." — detected |
| **"Link in first comment"** | Penalized (2026) | Algorithm identifies bridge behavior |
| **Generic carousels** | Declining | Style-over-substance carousels being targeted |
| **Single image posts** | Dead format | Down 30% vs text — major reversal |
| **Polls** | Down 35% | Multiplier collapsed |
| **Engagement pods** | **DEAD — actively destroyed** | Shadow bans, 60-90 day recovery, Lempod banned |
| **Automated commenting** | Crackdown (2026) | LinkedIn removes from "Most Relevant", limits visibility |
| **AI-generated content (detected)** | -30% reach, -55% engagement | Pattern detection improving. LinkedIn can detect and does not reward |
| **Generic motivational quotes** | Near-invisible | Unless adding genuine personal insight |
| **Reshared viral content** | Treated as low-effort | Need original perspective |
| **Daily posting** | Counterproductive | 2+ posts/day = **-40% reach per post** |
| **Hashtag stuffing** | Penalized | >3 hashtags risks spam flag. 360Brew doesn't need them |

### The Overuse Cycle (important)

LinkedIn's VP of Product: 60% of high-engagement posts in Q3 2025 used optimization tactics, but user satisfaction declined. The algorithm was overhauled to reward genuine value over tactics.

**Takeaway:** Tactics without substance = declining returns. Substance + smart execution = sustainable growth.

---

## 12. AI CONTENT DETECTION

| Signal | Impact |
|--------|--------|
| AI-generated content detected | **-30% reach, -55% engagement** |
| Repetitive wording, overly polished tone | Triggers detection |
| AI comments (timing, language patterns) | Under scrutiny |
| EU mandatory AI labeling | Starting August 2, 2026 |

**Best practice:** AI for research and drafting → rewrite in an authentic voice with personal examples. Our DIP + Post Creation Engine system solves this: we write in the author's voice with real stories, not generic AI text.

---

## 13. PERSONAL PROFILES vs COMPANY PAGES (updated)

| Metric | Personal Profile | Company Page |
|--------|-----------------|-------------|
| Feed allocation | **65%** | **5%** |
| Organic reach to followers | ~8-12% (was 15-20%) | **~1.6%** |
| Reach comparison | **561% more reach** (same content) | Baseline |
| Impressions | **2.75x more** | Baseline |
| Engagement | **5x more** | Baseline |
| Organic reach change 2024-2026 | Declined ~50% | Declined **~60%** |
| CEO content engagement | **4x average** | — |

**First-hour trial (Company pages):** LinkedIn shows the post to **2-5% of followers** and measures engagement velocity (likes/min, comments/impression, response speed).

**Strategy:** Personal profiles = primary distribution. Company page = content hub + secondary amplification. Employee advocacy = highest ROI (**7x better leads** vs company page).

---

## 14. LINKEDIN'S THREE OFFICIAL RANKING CRITERIA

LinkedIn has officially stated three ranking criteria:

1. **Relevance** — How accurately posts match the interests of the defined audience
2. **Expertise** — Whether the content demonstrates subject matter knowledge
3. **Engagement** — Whether the post drives meaningful comments from users typically interested in this topic

### LinkedIn's Stated Goals (2025-2026)

1. "Meaningful connections and relevant conversations" over virality
2. Knowledge and advice content as primary feed value
3. Making engagement pods "entirely ineffective"
4. Reducing engagement bait, clickbait, inauthentic content
5. Helping users build professional expertise (not entertainment)
6. **Precision delivery** — "content to people most likely to care" over broadcast

---

## 15. CHANGELOG

| Date | Change | Source |
|------|--------|--------|
| 2026-03-17 | **MAJOR UPDATE:** 360Brew 150B model details, 2-stage LLM pipeline (LLaMA 3 retrieval + GR ranking), engagement pods crackdown (Lempod ban, shadow bans), video reach crash (-35% to -70%), hashtags deprioritized (1-3 max), daily posting penalty (-40%), beyond-network distribution mechanics, comment thread depth weighting, dwell time specifics, LinkedIn official 3 ranking criteria, company page first-hour trial, "Lost-in-Distance" effect, Interest Picker feature | LinkedIn Engineering Blog (March 2026), Search Engine Land, Richard van der Blom Algorithm InSights 2025, AuthoredUp (621K posts), pettauer.net, Buffer, Jasmin Alic, ConnectSafely, MediaPost, arXiv |
| 2026-02-19 | Initial creation. Full research compilation | Richard van der Blom, Buffer, SocialInsider, Hootsuite, Sprout Social, Jasmin Alic, LinkedIn Engineering Blog |

---

## Sources

### Primary Research
- Richard van der Blom — Algorithm InSights Report 2025 (1.8M posts, 58K profiles, 31K company pages)
- AuthoredUp — 621,000+ posts tracked, median impressions analysis
- Buffer — 2M+ posts analysis (2025-2026)
- SocialInsider — LinkedIn Benchmarks 2025
- Postiv AI — LinkedIn Content Strategy analysis (2M+ posts)

### Algorithm Architecture (NEW — March 2026)
- LinkedIn Engineering Blog: "Large Scale Retrieval for the LinkedIn Feed" (Hristo Danchev, March 12, 2026)
- arXiv: "Large Scale Retrieval for the LinkedIn Feed using Causal Language Models" (arXiv:2510.14223)
- Search Engine Land: "LinkedIn updates feed algorithm with LLM-powered ranking and retrieval"
- MediaPost: "LinkedIn Uses New AI Models To Rebuild Feed Algorithm"
- pettauer.net: "LinkedIn 360Brew and the New Physics of Visibility"

### Algorithm Analysis
- Hootsuite: How the LinkedIn Algorithm Works 2025
- Sprout Social: How the LinkedIn Algorithm Works 2026
- Agorapulse: LinkedIn Algorithm 2026
- SocialBee: LinkedIn Algorithm 2026 Guide
- AuthoredUp: LinkedIn Algorithm 2025 Data-Backed Facts
- Dataslayer: LinkedIn Algorithm February 2026
- SourceGeek: How LinkedIn's Algorithm Works 2026
- River Blog: The 2026 LinkedIn Algorithm: 300 Posts Tested

### Engagement Pods & Automation
- ConnectSafely: LinkedIn Engagement Pods Crackdown 2026
- DEV Community: LinkedIn's Algorithm in 2025 — Why Engagement Pods Are Dead
- Future Forem: LinkedIn's 2026 Algorithm — The Engagement Bait Era Is Finally Over

### LinkedIn Official
- LinkedIn Engineering Blog: Leveraging Dwell Time
- LinkedIn VP of Product: Engagement pods "entirely ineffective" goal; showing old posts intentionally
- LinkedIn Sr. Director of Product: No link penalty (if content leads with value)
- LinkedIn Official Blog: Best practices

### Expert Practitioners
- Jasmin Alic: 26 Essential LinkedIn Tips 2026 (March 2026); Hook strategies
- Richard van der Blom: Algorithm InSights Report 2025
- Matt Navarra: How LinkedIn Algorithm Works 2025
- Chris Donnelly: Old vs New LinkedIn

### Format & Timing
- Sprout Social: Best Times to Post 2025
- Buffer: Best Time to Post; How Often to Post (2M+ posts)
- Digital Blacksmiths: Best LinkedIn Post Length 1200-1800 characters
- SocialRails: LinkedIn Post Character Limits 2026
- ContentIn: LinkedIn Algorithm 2025 Format Strategy Guide
- PostNitro: LinkedIn Carousel Engagement Stats 2025
- GrowLeads: LinkedIn Algorithm 2026 Text vs Video Reach
- LinkBoost: LinkedIn Posting Frequency Best Practices 2026
