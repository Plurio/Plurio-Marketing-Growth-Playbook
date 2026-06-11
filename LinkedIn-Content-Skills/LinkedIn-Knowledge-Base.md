# LinkedIn Knowledge Base — March 2026

> Complete knowledge base on the LinkedIn algorithm, formats, trends, hooks, comments, and profile optimization.
> Load this file into any AI and it will know how to create content that works on the platform.
>
> **Last updated:** 2026-03-25
> **Sources:** Richard van der Blom (1.8M posts, 58K profiles), AuthoredUp (621K+ posts), Buffer (2M+ posts), LinkedIn Engineering Blog, 17 LinkedIn Learning courses, our own data (40+ posts).

---

## Table of Contents

1. [The 360Brew Algorithm — how LinkedIn ranks content](#1-the-360brew-algorithm)
2. [8 ranking factors](#2-8-ranking-factors)
3. [Engagement hierarchy — what carries the most weight](#3-engagement-hierarchy)
4. [Content lifecycle — the life of a post](#4-content-lifecycle)
5. [Formats — benchmarks and specs](#5-formats)
6. [Posting time and frequency](#6-posting-time-and-frequency)
7. [Trends — what works, what's dying (March 2026)](#7-trends)
8. [Hook Pattern Library — hook formulas](#8-hook-pattern-library)
9. [Anti-Patterns — what gets penalized](#9-anti-patterns)
10. [Comments Engine — how to work with comments](#10-comments-engine)
11. [Profile Optimization — optimizing your profile](#11-profile-optimization)
12. [Visual Design System — visual rules](#12-visual-design-system)
13. [Weekly Update — the update process](#13-weekly-update)

---

## 1. The 360Brew Algorithm

As of March 2026, LinkedIn runs on **360Brew** — a 150-billion-parameter decoder-only transformer model (a LLaMA 3 fine-tune) that has replaced the previously fragmented ranking systems.

### Two stages

**Stage 1: Unified Retrieval (LLaMA 3 fine-tune)**
- Converts users and content into embeddings
- Updates embeddings within minutes
- Semantic linking (understands related topics despite different terminology)
- Sub-50ms retrieval

**Stage 2: Generative Ranking (Causal Transformer)**
- Causal attention: treats engagement history as an ordered sequence
- Learns the EVOLUTION of professional interests (not isolated per-post scoring)
- GPU clusters (H100s) for real-time ranking

### The key shift

| Old approach (signal-based) | 360Brew (semantic reasoning) |
|------------------------------|------------------------------|
| Hashtags = discovery lever | Hashtags = minor signal (1-3 max) |
| Formatting tricks = reach growth | Formatting helps the AI parse content, but substance matters more |
| Post fast and often | Post deep and well (3-5/week) |
| Pods = boost | Pods = shadow ban |
| Viral hook > substance | The first sentence = semantic anchor for ranking the entire post |
| Network size = reach | Topic expertise = reach (60% via interest-based clusters) |
| Any engagement = good | Only thoughtful engagement (saves, deep comments, shares) |

### Key numbers

- Organic reach dropped 50% for 98% of users (van der Blom, 1.8M posts)
- Engagement dropped 25%
- 60% of reach now flows through interest-based clusters OUTSIDE your network
- Posts live 24-48 hours with a good strategy
- Personal profiles deliver 561% more reach than company pages
- Personal impressions are 2.75x higher, engagement 5x higher
- CEO content gets 4x the average
- Employee advocacy yields 7x better leads

---

## 2. 8 ranking factors

| # | Factor | Weight | What it means | What to do |
|---|--------|--------|---------------|-----------|
| 1 | **Profile-Content Alignment** | Critical | 360Brew cross-checks post topics against Headline, About, Experience. Semantic mismatch → suppressed distribution | Headline and About MUST contain keywords from your post topics. Roughly 90 days needed to build semantic authority |
| 2 | **Topic Consistency** | Critical | ~90 days of consistent posting across 3-4 topic clusters = semantic authority. 360Brew builds a "topic DNA" | Pick 3-4 topics. Don't jump between unrelated topics. Consistency > diversity |
| 3 | **First Sentence = Anchor** | Critical | "Lost-in-Distance" effect: the first line gets disproportionate weight for semantic ranking. A generic prologue → deprioritized BEFORE a human even scrolls | The first ~140 characters (before "See more") = the most important. Hook-first. No "In today's world..." |
| 4 | **Saves > Likes** | Very High | 1 save = 5-10x a like in algorithmic weight. Save = strong value signal | Create save-worthy content: frameworks, checklists, templates, reference material. "Save this for when you need..." |
| 5 | **Comments Train Profile** | High | What you comment on = what the algorithm shows you and your content to. Comments from relevant job titles = more distribution | Comment in your niche. 15+ words = 2.5x weight. Comments on other people's posts train the algorithm |
| 6 | **Links = Penalty** | High | ~60% reach loss when links are included. "Link in first comment" is also penalized (2026) | If you need a link — place it after 300+ characters. Best of all — full value in the post, no links |
| 7 | **Structure Aids AI** | Medium | Short paragraphs, lists, whitespace → 360Brew parses semantics better | Structure it: 1-3 line paragraphs, lists, whitespace between blocks |
| 8 | **Hashtags = Minimal** | Low | 360Brew understands context from the text. 5+ hashtags = spam risk | 1-3 relevant ones max. Natural keywords matter more than hashtags |

---

## 3. Engagement hierarchy

Ordered by algorithmic weight (most valuable to least):

| # | Action | Weight | Notes |
|---|--------|--------|-------|
| 1 | **Saves** | 5-10x baseline | #1 value signal. Frameworks and checklists = save magnets |
| 2 | **DM shares** | ~5x | New in 2025 analytics. Strong "worth sharing privately" signal |
| 3 | **Reposts from influential users** | ~4x | A reshare from someone with niche authority = powerful boost |
| 4 | **Comments 15+ words** | 2.5x | Thoughtful comments carry 2.5x the weight of short ones |
| 5 | **Thread depth (chains)** | Variable, high | Back-and-forth in comments outweighs isolated comments |
| 6 | **Dwell time 31-60 sec** | High | Optimal "hover" time on a post = deep engagement signal |
| 7 | **Comments (any)** | 2x | Even short comments carry 2x the weight of likes |
| 8 | **Click "See more"** | Medium-high | Indicates the hook worked |
| 9 | **Profile visits from post** | Medium | Reader became interested in the author |
| 10 | **Likes** | 1x (baseline) | Minimum weight, baseline |
| 11 | **"Great post!" comments** | Downranked | Low-entropy, flagged as noise |

### Dead signals (actively suppressed)

| Signal | Penalty |
|--------|---------|
| Engagement pods | Shadow ban 60-90 days, -96% reach. Lempod is banned |
| "Great post!" comments | Removed from "Most Relevant", downranked |
| Engagement bait ("Agree?", "Tag someone") | Detected and penalized |
| Automated commenting | Language/timing pattern detection, limited visibility |
| Hashtag stuffing (5+) | Spam risk flag |
| 2+ posts/day | -40%+ reach per post |

---

## 4. Content lifecycle

| Window | What's happening | What to do |
|--------|------------------|-----------|
| **0-60 min (Quality Check)** | 2-5% of your network sees the post. The algorithm evaluates the first signals | Author's first comment within the first 5 minutes. Cross-team comments at T+5-15 min |
| **0-2 hours (Golden Window)** | Critical engagement determines further reach. If high → interest-based distribution (60% of reach) | Author reply to comments <30 min (+64% total comments, 2.3x views). 5-10 comments on other people's posts |
| **8 hours (8-Hour Review)** | The algorithm evaluates sustained engagement | Keep replying to comments. Second engagement round |
| **24-48+ hours (Extended)** | Quality posts live longer. LinkedIn deliberately surfaces week-old posts ahead of fresh mediocre ones | Monitor every 2-3 hours. DO NOT publish a new post within 12 hours |

### Golden Window Timeline

| Time | Action |
|------|--------|
| T+0 | Post published |
| T+0-5 min | Author's first comment (15+ words, doesn't restate the post, bonus insight or directing question) |
| T+5-15 min | Colleague comments (each = a unique angle, 30% team / 70% external in the long run) |
| T+15-30 min | Engagement routine: author comments on 5-10 posts in the niche → algorithm sees activity → more reach |
| T+30-60 min | Reply to ALL comments. Each reply = a new algorithmic signal |
| T+60-90 min | Second round: another 3-5 comments + check for new ones |
| T+90+ min | Monitor every 2-3 hours. DO NOT publish a new post for 12 hours |

---

## 5. Formats

### Format ranking (February 2026)

| # | Format | Engagement Rate | Trend | Effort | Best For |
|---|--------|-----------------|-------|--------|---------|
| 1 | **Carousel/Document** | 6.60% | Stable-high (generic declining) | High | Frameworks, step-by-step, data. 6-9 slides optimal. Text-oriented > image-oriented |
| 2 | **Multi-Image** | 6.60% | Stable, underutilized | Medium | Comparisons, before/after, screenshots. 3-5 images |
| 3 | **Native Video** | 5.60% | Growing +23% YoY (but reach -35-70%) | High | Demos, clips, authenticity. <60 sec vertical |
| 4 | **Text Only** | 2-4% | Declining -18% YoY | Low | Hot takes, stories, deep dives. Dwell time saves text posts |
| 5 | **Text + Image** | Varies | Neutral | Low-Med | Context, screenshots. Exception: memes |
| 6 | **Polls** | Declining | -35% reach, multiplier 1.64x → 1.19x | Low | Only genuine research with follow-up |
| 7 | **Single Image** | -30% vs text | Dead format | Low | AVOID |
| 8 | **External Links** | ~60% penalty | Penalized | Low | Only when absolutely necessary, after 300+ chars |

### Format specs

**Carousel/Document:**
- Size: 1080x1350px (vertical 4:5) — optimal for mobile
- Slides: 5-10 optimal (6-9 sweet spot). Generic carousels declining — only with ORIGINAL data/frameworks
- Format: PDF upload
- First slide = thumbnail → bold, large text, readable at small size
- Up to 300MB

**Multi-Image:**
- Up to 9 images, 3-5 recommended
- 1200x1200px or 1080x1350px
- Stable and underused format

**Native Video:**
- MP4/MOV, 9:16 (vertical) or 16:9
- <60 seconds optimal (best <30 sec)
- +80% engagement vertical vs horizontal
- +42% visibility native vs YouTube link
- Captions mandatory (75% watch without sound)
- Text-first indexing bias (360Brew indexes text better than video)

**Text Only:**
- Max 3,000 characters
- **1,200-1,800 characters = sweet spot** (+47% engagement)
- 210-235 characters before "See more" = critical hook zone
- 60-70% drop off at "See more"

### Post Length Guide

| Size | Characters | When |
|------|-----------|------|
| Micro | <500 | Quick hot takes |
| Short | 500-1,000 | One insight + example |
| **Sweet Spot** | **1,200-1,800** | **+47% engagement. The default format** |
| Long | 1,800-2,500 | Deep dives (every word must earn its place) |
| Max | 2,500-3,000 | Only for exceptional posts |

### Author Response Speed

| Reply time | Effect |
|-----------|--------|
| **15 min** | +90% algorithmic boost |
| **30 min** | +64% total comments, 2.3x views |
| 60+ min | Significantly reduced |

### Platform Usage

- 75% mobile (up 10% from 2024)
- Personal vs company: 561% more reach, 2.75x more impressions, 5x more engagement
- Company page reach: ~1.6% of followers (declining -60%)
- Newsletter open: 35-40%

---

## 6. Posting time and frequency

### Best days

| Day | Rank | Notes |
|-----|------|-------|
| **Tuesday** | #1 | Engagement +20%. Best day to publish |
| Wednesday | #2 | 10 AM and 3 PM — strong slots |
| Thursday | #3 | 10 AM — a good window |
| Monday | #4 | People are clearing email, but publishing is OK |
| Friday | #5 | Especially weak after 2:00 PM |
| Sat-Sun | #6-7 | Engagement -45%. Do not publish |

### Best time (for US + EU audience)

| LA Time | EST | CET | Notes |
|---------|-----|-----|-------|
| **6:00 AM** | 9:00 AM | 15:00 | Ideal: US peak + European boosters still active |
| **7:00 AM** | 10:00 AM | 16:00 | Excellent: US peak hours |
| 8:00 AM | 11:00 AM | 17:00 | Good for US, Europeans logging off |

### Posting frequency

| Frequency | Effect |
|-----------|--------|
| 1/week | Baseline. Minimal momentum |
| **3-5/week** | **Sweet spot. Optimal quality/reach balance** |
| 2/week for executives | Often the best ROI for leaders |
| **2+ per day** | **PENALTY: -40%+ reach per post. Daily posting = a dead strategy** |
| 11+/week | Only for full-time creators |

**Critical:** "Post every day" no longer works. One deep post with high dwell time = significantly more value than 5 shallow ones. 360Brew rewards depth, not frequency.

### Pre-posting checklist

- [ ] Day: Tue-Thu (ideal), Mon (OK), Fri before 2:00 PM (last resort)
- [ ] Time: 6-7 AM LA
- [ ] EU boosters ready for first 30 min engagement
- [ ] Not Friday afternoon and not weekends
- [ ] At least 12 hours since the author's last post
- [ ] Not 2+ posts in one day

---

## 7. Trends (March 2026)

### HOT NOW (use)

| # | Trend | Why it works | Horizon |
|---|-------|--------------|---------|
| 1 | **Practical frameworks as carousels** | Step-by-step 6-9 slides, text-oriented, save-worthy = #1 signal, evergreen | Ongoing |
| 2 | **Build in public** | Behind-the-scenes decisions, failures, real numbers. Authenticity > polish | 6+ mo |
| 3 | **Deep-dive text posts** | Long educational content. High dwell time. 360Brew rewards depth | Rising |
| 4 | **AI tools + real results** | Not "here's a prompt" but "here's what happened when I used AI" | 3-6 mo |
| 5 | **Contrarian takes with evidence** | Challenge wisdom with data/experience. 360Brew rewards expertise depth | Ongoing |
| 6 | **Original data visualizations** | Your own data, charts. High save rate. Scroll-stopping | Ongoing |
| 7 | **Personal transformation stories** | "I used to do X. Now Y. What changed." Authenticity signal | Ongoing |
| 8 | **Multi-part series** | Serialized content, loyal audience returns | 3-6 mo |
| 9 | **Short-form native video** | <60 sec vertical. Reach is down, but authenticity value is high | Stable |

### RISING (test)

| # | Trend | What to do |
|---|-------|-----------|
| 1 | **Comment thread depth** | 360Brew weights back-and-forth higher than isolated comments. Seed reply chains |
| 2 | **Collaborative posts** | Cross-audience amplification between authors on the team |
| 3 | **Semantic niche authority** | ~90 days of consistent topical posting = beyond-network reach |
| 4 | **"DM me [word]" lead gen** | Replaces "link in bio" (penalized). Direct conversations |
| 5 | **Save-optimized CTAs** | Explicit "Save this for when you need X". Saves = 5-10x like weight |
| 6 | **User-generated content** | Customer results/feedback with commentary |

### DECLINING (stop)

| # | Trend | Why it's dying | What to use instead |
|---|-------|----------------|---------------------|
| 1 | Generic "swipe carousel" tips | Oversaturation, LinkedIn targets low-value | Only carousels with ORIGINAL data/frameworks |
| 2 | Prompt-sharing posts | Format fatigue | Show the RESULT, not the prompt |
| 3 | "5 agents every founder needs" listicles | Overused in the AI niche | ONE specific use case with real numbers |
| 4 | Engagement-focused polls | -35% reach | Only genuine research with follow-up |
| 5 | "Link in first comment" | Penalized 2026 | Full value in the post |
| 6 | Hashtag stuffing (5+) | 360Brew doesn't need it | 1-3 relevant max |
| 7 | Daily posting | 2+ per day = -40% reach | 3-5/week max, quality > frequency |

### DEAD (avoid)

| # | Trend | Penalty |
|---|-------|---------|
| 1 | "Bro-etry" (one-line dramatic paragraphs) | Actively suppressed mid-2025 |
| 2 | Engagement bait ("Agree?", "Tag someone") | Detected and penalized |
| 3 | Generic motivational quotes | Zero differentiation, the algorithm ignores them |
| 4 | Engagement pods | Shadow ban 60-90 days, -96% reach |
| 5 | Automated commenting | Removed from "Most Relevant" |
| 6 | Single image posts | Down 30% vs text |
| 7 | Reshared viral content without commentary | Treated as low-effort |
| 8 | "Great post!" comments | Low-entropy = downranked |

### Industry-specific (AI / MarTech / Performance Marketing)

**What resonates right now:**
- AI agents replacing workflows (360Brew amplifies niche expertise)
- Attribution in the AI era (a perennial pain point)
- Founders using AI tools daily (aspirational + practical)
- Performance marketing automation (few practitioners with real results)
- "Data quality > model sophistication" (contrarian to AI hype)
- Creative testing at scale (concrete, data-heavy)

**Overplayed in the niche:**
- "AI will replace marketers" (boring)
- "Top 10 AI tools for marketing" (zero differentiation)
- "How to write ChatGPT prompts" (commodity knowledge)
- "AI-generated content is fine" (risky: LinkedIn detects it, -30% reach, -55% engagement)

---

## 8. Hook Pattern Library

**Rules:**
- The first ~140 characters before "See more" = everything a reader sees
- The first sentence carries disproportionate algorithmic weight (360Brew Lost-in-Distance)
- Always write 2-3 hook variants
- Test it: "Would I stop scrolling?"

### Formula 1: Contrarian Take

**Pattern:** "Everyone thinks [X]. They're wrong." / "Popular advice about [X] is dead wrong."

**When:** You have a position that contradicts the mainstream. You have data/experience to back it up.

**Examples:**
- "AI-first doesn't mean using ChatGPT. Here's what it actually means."
- "I stopped opening dashboards 3 weeks ago. Best decision this quarter."
- "Everyone talks about scaling ads. Nobody talks about when NOT to scale."

**Danger:** Contrarianism for its own sake = empty. You need real evidence/personal experience.

### Formula 2: Personal Story / Vulnerability

**Pattern:** "I [did/lost/failed at something]. Here's what happened." / "Last [time period], [unexpected happened]."

**When:** A real story. Leads to an actionable lesson.

**Examples:**
- "I built a 100-person agency. Then I left it all to build something new."
- "Two startups. A four-year-old daughter. A move to Lisbon."
- "I was afraid our product wasn't ready. We launched anyway."

**Data:** 8.5x average engagement for authentic vulnerability. MUST be genuine (manufactured = backlash).

### Formula 3: Quantified Outcome / Data Shock

**Pattern:** "How I achieved [specific result] in [time] with [method]." / "[X]% of [audience] do [thing]. They get [Y]% results."

**When:** Specific numbers from real experience. Numbers stop the scroll.

**Examples:**
- "We cut $3.45 per creative in testing costs. One agent did it."
- "30+ people. One workspace. Zero meetings about who edits what."
- "Only 3% of marketers track LTV beyond day 30. They outperform by 4x."

**Danger:** Fake/inflated numbers = trust destruction. Real data only.

### Formula 4: Question-Led

**Pattern:** "Are you making this mistake with [X]?" / "What would you do if [specific scenario]?"

**When:** The topic is relevant to a broad audience. The question triggers self-reflection.

**Examples:**
- "What if your dashboards could talk back to you?"
- "Are you optimizing for the wrong metrics?"
- "How many hours/week on reports nobody reads?"

**Rule:** The question must be SPECIFIC. "What do you think?" = engagement bait. A specific scenario = genuine.

### Formula 5: Authoritative / Experience-Based

**Pattern:** "After [N years / N clients / N experiments], I learned [N things]." / "I've [done X] for [N years]. Here's what nobody tells you."

**When:** Deep experience in the topic. Credibility through track record.

**Examples:**
- "20 years in performance marketing. 5 things I'd do differently."
- "I've managed $100K+/month budgets for 15+ clients. Here's the pattern."
- "After building data pipelines for 30+ clients — the #1 mistake everyone makes."

### Formula 6: Problem & Agitation

**Pattern:** "You work [X hours] but see [no results]." / "[Pain point] is killing your [outcome]."

**When:** Targeting a known pain point. The post offers a solution.

**Examples:**
- "Your attribution data is lying to you. Costing you thousands."
- "Marketers are afraid to scale. Here's why the fear is rational."
- "You're spending 40% of your time on tasks AI could do in seconds."

### Formula 7: Behind-the-Scenes / Build in Public

**Pattern:** "Here's what [X] actually looks like behind the curtain." / "We just [built/launched/broke X]. Here's the real story."

**When:** Sharing internal process, decisions, failures. Authenticity > polish.

**Examples:**
- "We ship features every day. Here's what our workflow actually looks like."
- "This is what our AI agent's reasoning chain looks like. Screenshot inside."
- "Why we prioritized the data platform over agent features. The hard trade-off."

### Anti-Hooks (NEVER use)

| Anti-Hook | Why it doesn't work |
|-----------|---------------------|
| "Some thoughts on..." | Zero curiosity |
| "I wanted to share..." | Weak opener |
| "In this post I will..." | Kills intrigue, academic |
| "Exciting news!" | Overused, the algorithm flags it as promotional |
| "Happy Monday!" / "TGIF!" | Generic, no value |
| "Agree?" | Engagement bait — penalized |
| A very long first sentence | Loses the reader before "See more" |
| Starting with a hashtag | Looks spammy |

### Hook Testing Checklist

- [ ] Specific not generic?
- [ ] Creates curiosity/tension?
- [ ] Would I stop scrolling?
- [ ] Sounds like the author?
- [ ] Under 140 chars (before "See more")?
- [ ] Body delivers on the hook's promise?

---

## 9. Anti-Patterns

### Algorithm Killers

| Anti-Pattern | Impact | Fix |
|--------------|--------|-----|
| Engagement bait ("Agree?", "Tag someone") | Detected → penalized | Genuine, specific topical questions |
| "Link in first comment" | Penalized (2026) | Embed link after 300+ chars or skip |
| Editing a post after publishing | Resets the algorithm. Distribution cycle = zero | Proofread BEFORE. Leave a typo unless critical |
| 1+ post per 12 hours | Cannibalizes reach | Minimum 12-hour gap, better 24h |
| Topic jumping | Algorithm can't classify expertise | Stay in 3-4 clusters |
| Profile-Content mismatch | Reduced authority | Headline keywords = post topics |
| Engagement pods | Shadow ban 60-90 days, -96% reach | Genuine engagement only |
| Automated commenting | Language/timing detection | Manual, thoughtful only |
| External links in the first 300 chars | Reduced reach | Lead with value, link later |

### Content Killers

| Anti-Pattern | Fix |
|--------------|-----|
| Wall of text | 1-3 line paragraphs, whitespace, lists |
| Multiple ideas in one post | ONE thought = one post. Multiple = series |
| "Bro-etry" | Actively suppressed. Normal paragraphs, drama through substance |
| Generic advice without specifics | Concrete numbers, real examples, personal experience |
| Starting with "I wanted to share..." | Start with a specific, intriguing statement |
| No CTA | Specific CTA: comments/saves/shares |
| Hashtag overload (>5) | 1-3 max |
| Too long without earning it | 1,200-1,800 chars sweet spot |

### Tone Killers

| Anti-Pattern | Fix |
|--------------|-----|
| "We/our" in personal posts | ALWAYS I/my in personal posts |
| AI-sounding text | -30% reach, -55% engagement. The author's real voice |
| "In today's world..." | A concrete observation from real experience |
| Humble-bragging ("So humbled...") | Speak directly about achievements or skip |
| "Excited to announce..." | Start with VALUE, not emotion |
| Manufactured vulnerability | Only REAL stories |

### Format Killers

| Anti-Pattern | Fix |
|--------------|-----|
| Single image post | Dead format. Multi-image or carousel |
| Generic carousel (style > substance) | Only with original data/frameworks |
| Horizontal video | -80% engagement vs vertical. 9:16 |
| YouTube link instead of native | -42% visibility. Always upload natively |
| Poll for engagement | -35% reach. Only genuine research |

### Strategic Mistakes

| Mistake | Fix |
|---------|-----|
| No comment reply in the first hour | Block 30-60 min for active engagement |
| Same format every time | Rotate: text → carousel → video |
| Multiple authors, same topic, same day | Stagger 2-3 days |
| No post for 2+ weeks | Minimum 1/week |
| Posting when boosters are offline | Coordinate with EU/US |

### 30-Second Pre-Publishing Check

- [ ] No anti-hook? No engagement bait? No "bro-etry"?
- [ ] No AI-sounding generic? No "we/our" in a personal post?
- [ ] Not a single image? Not within 12 hours of last post?
- [ ] Topic matches headline? Specific examples/numbers/stories?
- [ ] CTA specific not generic?

---

## 10. Comments Engine

### Why comments are critical (algorithmic data)

| Fact | Source |
|------|--------|
| 15+ word comments = 2.5x weight | Richard van der Blom |
| Reply in first 30 min = +64% total comments, 2.3x views | van der Blom |
| 5-10 comments after publication = +55% profile views | Algorithm-Intelligence |
| Comments train your profile — what you comment on = what gets shown | 360Brew |
| Reply in first 15 min = +90% algorithmic boost | AuthoredUp |
| Thoughtful comments in your niche = +20% reach on your own posts | Buffer / SocialInsider |

### Three types of comments

#### Type 1: Reply on your own post

**Rules:** First 30 min are critical. Min 15 words. Add value, not "Thanks!". Follow-up question (stimulate thread).

**Formulas:**

| Situation | Formula | Example |
|-----------|---------|---------|
| Agreement | Expand + Add Layer | "Exactly. What most miss: [deeper insight]. We saw this when [example]." |
| Question | Answer + Bridge | "Great Q. Short answer: [A]. Real answer: [nuance]." |
| Disagreement | Acknowledge + Reframe | "See your point, but our experience [counter]. The nuance is [difference]." |
| Compliment | Redirect to Insight | "Appreciate. Credit goes to [team/process]. What made it work: [specific]." |
| "How do I learn more?" | Give Value + Soft CTA | "Start with: [tip]. Want the full breakdown? DM — happy to share." |

#### Type 2: Comment on someone else's post

**Rules:** Only in your niche. Min 15 words. Unique perspective from experience. NEVER generic. Never sell/pitch. Tone slightly softer (we're guests).

**Formulas:**

| Situation | Formula |
|-----------|---------|
| Own experience | "Tested exactly this with a client. The surprising part: [finding]. [Number] confirmed." |
| Addition | "Adding: [insight]. Ran it for [client type], the difference was [metric]." |
| Smart question | "Did you see the same pattern in [variation]? In our case [opposite happened]." |
| Contrarian | "Data shows the opposite for [segment]. Could be industry-specific — what's the sample?" |

#### Type 3: Initiate a discussion (on your own post)

**Rules:** First 5 min. Don't restate the post. No links (penalized 2026).

**Formulas:**
- Bonus insight: "Didn't include in the post: [insight]. Curious if others have seen this."
- Directing question: "Biggest Q I get: [Q]. My take: [brief]. Yours?"
- Behind the scenes: "Story behind it: [how the idea came up]. The original version was very different."

### Source Grounding (CRITICAL)

Every statement in a comment must be traceable:

| Category | Action |
|----------|--------|
| **Verified fact** (specific source with details) | Keep as is |
| **Grounded inference** (direct implication from verified facts) | Keep, don't embellish |
| **Thin ground** (the author's topic, but no specific case) | Reformulate as a question or reference a known fact |
| **Bullshit** (sounds plausible but invented) | Delete or replace with a question |

**Red flag:** >50% of claims = thin ground / bullshit → REWRITE. Better a short verified comment than a long one with filler.

### Micro-Reply Bank (for congratulations and short replies)

**Rotation is mandatory! No two identical replies in a row.**

**Energetic:** "Buckle up — this is just the beginning", "Fun part starts now", "Stay tuned", "Just chapter one", "Just warming up"

**Warm:** "Means a lot", "Appreciate it!", "Made my day", "Heart"

**With character:** "Not gonna lie — feels good", "Real work begins now", "LFG"

**Minimalist:** Single emoji reactions

**With specifics:** "Thank you! [one concrete detail]", "[Name], appreciate it — especially from someone [who knows the space]"

### Iron Rules

1. **ALWAYS reply to comments.** Never just like. Variety = a living profile. Repetitive = bot.
2. **Don't duplicate post content.** Forbidden: quoting metrics from the post back at the author.
3. **Address the person directly (2nd person).** "You're building..." NOT "He built..."
4. **No "not X but Y" constructions.** "Stops being X, becomes Y" = pretentious and empty. Speak plainly.
5. **No self-promo on other people's posts.** Support the author, don't redirect to yourself.
6. **Same factual standards as for posts.** Don't invent experience.

### Anti-Patterns for comments

| NEVER | Instead |
|-------|---------|
| "Great post!" / "Love this!" / "So true!" | A specific example from experience |
| Quoting the post + "this is the key/shift" | Your own experience, confirming/extending |
| Restating the author's metrics | Your own perspective on the metric |
| "I've seen..." without specifics | A specific fact or stay silent |
| "That's exactly how we designed it" | AI-signal. Validate with action/result |
| Selling in comments | Value only, DM for follow-up |
| Copy-pasting one comment to many posts | LinkedIn detects the pattern. Each one = unique |
| Only team circle | 30% team, 70% external |

### Cross-Team Amplification

When one author posts, others leave thoughtful comments with UNIQUE angles:
- Visionary author ← Practitioner: "Here's what this looks like for a specific client"
- Practitioner ← Visionary: "Exactly the layer we're building"
- Product ← Data: "Why the data layer matters before the agent layer"
- Content ← Visionary: "The content machine uses exactly this"

---

## 11. Profile Optimization

### Why the profile is critical

**360Brew cross-checks post topics against the profile (Headline, About, Experience). Semantic mismatch = distribution suppression.**

| Fact | Effect |
|------|--------|
| Photo | 3x connection requests, 2x profile views |
| Verified | 60% more views |
| 5+ skills | 2.9x views, 4.7x messages |
| Premium | 6x views on average |

### 1. Headline (220 chars max, the first 60 visible in the feed)

**Formula:** `[Role/Identity] | [Core Expertise 1] + [Core Expertise 2] | [Unique Differentiator]`

**Rules:**
- Keywords from your post topics are MANDATORY (360Brew Profile-Content Alignment)
- The first 60 chars = what's visible in feed/comments → the most important part
- AVOID: "Thought Leader", "Visionary", "Guru", "Passionate"
- Update when content focus shifts

### 2. About / Summary (5 paragraphs)

| # | Section | What to write |
|---|---------|---------------|
| 1 | **HOOK** | Who you are and why it matters (2-3 sentences). NOT "passionate" → "20 years building..." |
| 2 | **STORY** | Key pivot/transformation. "After building X, I realized Y. That's why Z." |
| 3 | **WHAT I DO NOW** | Current focus with specifics. "At [Company], building [specific]..." |
| 4 | **PROOF** | Numbers, cases, social proof. "100+ clients. $15M agency. 30+ person team." |
| 5 | **CTA** | Next step. "DM me if [reason]. I share [topic] here weekly." |

**Rules:**
- First person (I/my)
- Industry keywords naturally
- Short paragraphs with whitespace
- 40+ words minimum (below that it's not indexed in search)
- Update every 3-6 months
- NEVER: "I am a passionate professional...", CV-style, corporate speak

### 3. Photo & Banner

| Element | Do | Don't |
|---------|----|-------|
| Photo | Professional, friendly, recent. Face 60%+ of frame. Good light | No pets, kids, family. Not a stock photo |
| Banner | Branded, clean. Tagline or value prop | Don't overdesign |
| Cover Story | 30 sec video = high impact | |

### 4. Experience

- A story, not a CV. Achievements > responsibilities
- Current Role MUST be filled in (empty = semantic gap)
- Numbers/results > generic descriptions
- Career breaks can be included

### 5. Featured Section

- Best posts of the quarter (high engagement, save-worthy)
- Key articles/newsletters
- Links: company site, lead magnet
- Documents: PDF frameworks, checklists
- Update quarterly minimum

### 6. Skills & Endorsements

- 5+ skills → 2.9x views, 4.7x messages
- Top 3 shown first (how you get found)
- Max 100 skills, focus on quality
- Endorsements from 1st-degree connections = credibility boost

### 7. Verifications

- **Verified profiles → 60% more views**
- Identity verification (Government ID)
- Workplace verification (Work email, Microsoft Entra)
- Free, can be removed

### 8. Custom URL & Settings

- Custom URL: `linkedin.com/in/firstname-lastname`
- Website link under the headline
- Name pronunciation audio
- Creator Mode: activate for amplified content, Follow link, Newsletter access, 5 profile topics

### Quarterly Audit (every 90 days = 360Brew semantic cycle)

- [ ] Headline contains 2-3 key post topics?
- [ ] About tells a story, doesn't list skills?
- [ ] Current Role filled in?
- [ ] Featured = best posts of the quarter?
- [ ] Skills 5+? Top 3 = how you want to be found?
- [ ] At least 3 fresh recommendations?
- [ ] Post topics over the past 90 days match Headline + About?
- [ ] Verifications connected?
- [ ] Photo current?
- [ ] Creator Mode active + topics updated?

---

## 12. Visual Design System

### 4 visual modes

| Mode | When | Background | Logo |
|------|------|------------|------|
| **BUILDER (dark)** | Frameworks, how-to, step-by-step, numbered lists, technical | #0D0D0D dark | Last slide, text only ("Author · Company") |
| **PRODUCT (branded)** | Product announcements, features, demo, case studies, launches | #FFFFFF white | Full logo first + last slide |
| **MEME / CULTURE** | Memes, humor, cultural references, hot takes with images | Per the meme | NEVER |
| **PERSONAL / STORY** | Personal stories, event photos, behind the scenes, team | Per the photo | NEVER |

### Decision Matrix

| Content type | Mode | Format | Logo |
|--------------|------|--------|------|
| Framework / How-to / Process | BUILDER | Carousel (PDF) | Last slide text |
| Product feature / Launch | PRODUCT | Carousel / Multi-Image | First + last |
| Meme / Humor | MEME | Text + Image | Never |
| Personal story / Event | PERSONAL | Text + Photo | Never |
| Hot take / Opinion | None | Text Only | N/A |

### Carousel Design Rules

1. **Scannable in 3-5 seconds** — one thought per slide
2. **First slide = thumbnail** — bold, large text, readable at small size
3. **Whitespace > decoration**
4. **Text left-aligned** (center only for transition slides)
5. **Size: 1080x1350px** (vertical 4:5)
6. **PDF upload**
7. **5-10 slides optimal**

---

## 13. Weekly Update — the update process

### Schedule

| Day | Task | Time | What gets updated |
|-----|------|------|-------------------|
| **Monday** | Algorithm & Trends Refresh | 45-60 min | Algorithm-Intelligence, Format-Performance-Data, Current-Trends, Hook-Pattern-Library, Anti-Patterns |
| **Wednesday** | Content Scan (new material) | 30-45 min | Author DIPs, Topic Backlog |
| **Friday** | Performance Review + Planning | 30-45 min | Performance-Log, Experiment-Backlog, DIP Feedback Logs |

### Monday: what to look for and where

| What to check | Where |
|---------------|-------|
| New algorithm research | Richard van der Blom, Buffer, SocialInsider, Hootsuite |
| Official LinkedIn announcements | LinkedIn Engineering Blog, LinkedIn News |
| Practitioner recommendations | Jasmin Alic, Lara Acosta, Justin Welsh, Matt Navarra |
| New format trends | Watchlist profiles + trending in the feed |
| New hook patterns | High-engagement posts in the niche |
| What's dying/saturating | Feed observations + community |

### Wednesday: sources for the Content Scan

11 transcript locations to scan:
1. your-transcripts/synced-meetings/ (weekly syncs)
2. your-transcripts/marketing-meetings/
3. your-transcripts/webinars/
4. your-transcripts/strategy-calls/
5. your-transcripts/internal-product-calls/
6. your-raw-sources/podcasts-and-events/
7. Media activities/Conferences/
8. Media activities/Livestreams/
9. Media activities/Partnership-Activities/
10. Production/Projects/*/Meetings transcripts/
11. your-raw-sources/telegram-posts/

For each new transcript: identify the author → expertise cluster → new stories/patterns/frameworks → 1-3 post ideas → Topic Backlog.

### Friday: Performance Review

1. Weekly metrics: impressions, likes, comments, saves, shares
2. Pattern analysis: which formats/hooks/topics worked
3. Update the Experiment Backlog
4. Feedback Log review: if feedback repeats 3+ times → promote it into the DIP

### Triggers for an off-cycle update

| Trigger | Action |
|---------|--------|
| LinkedIn Engineering Blog: major update | Update Algorithm-Intelligence immediately |
| Richard van der Blom: new report | Update Format-Performance-Data + Algorithm-Intelligence |
| Sharp reach drop | Investigate → update Anti-Patterns |
| New content type taking off | Current-Trends → RISING |
