---
name: find-comment-targets
description: Finds LinkedIn target posts to comment on. Search strategies — by topic (author's expertise clusters), by ICP (potential customers), by networking (thought leaders in the niche). Helps plan the engagement routine.
disable-model-invocation: true
argument-hint: [Author] [--strategy topic|icp|networking|all]
allowed-tools: Read, Grep, Glob
---

# Find Comment Targets

Search for and recommend target LinkedIn posts to comment on.

## Input

- `$0` — author name (Seva, Kirill)
- `--strategy` — search strategy (default: all)
  - `topic` — posts on topics from the author's expertise clusters
  - `icp` — posts by people in the ICP (potential customers)
  - `networking` — posts by thought leaders for networking
  - `all` — all three strategies

## Required files

1. **Author DIP:**
   `Knowledge-Base/01-Identity-Profiles/[Author]-DIP.md`
   → Expertise Clusters, Topics, Target audience

2. **Algorithm-Intelligence:**
   `Knowledge-Base/02-LinkedIn-Algorithm/Algorithm-Intelligence.md`
   → Engagement rules, Comments Train Profile

3. **ICP Reference:**
   `ICP-Reference.md`
   → Target industries, budgets, characteristics

4. **Current-Trends:**
   `Knowledge-Base/03-Viral-Trends/Current-Trends.md`
   → What's trending now

## Why comment strategically

| Fact | Source |
|------|--------|
| Commenting on 5–10 posts after publication → +55% profile views | Algorithm-Intelligence |
| Comments Train Profile — what you comment on teaches the algorithm whom to show you to | 360Brew model |
| Thoughtful comments in your niche → +20% reach for your own posts | Buffer / SocialInsider |
| Mix: 30% team, 70% external — to avoid creating an engagement pod | Comments-Engine |

## Pipeline

### Step 1: Load DIP + pick strategy

From the DIP, extract:
- Expertise Clusters → topics to search for
- Target audience → who we're looking for
- Stories Bank → what we can concretely add

### Step 2: Define search criteria

#### Strategy: Topic (posts on topic)

Search for posts on topics from the author's Expertise Clusters:

| Author | Key topics for search |
|--------|------------------------|
| Seva | AI agents in marketing, performance marketing automation, founder journey, AI-first teams |
| Kirill | Growth marketing, creative testing, attribution, campaign automation |
| Denis | Product management, data-driven product decisions, CPO systems |
| Ella | Content strategy, marketing operations, team workflows |

**Criteria for a good post to comment on:**
- Topic overlaps with one of the author's expertise clusters
- Post author = relatable peer (not a corporate account)
- The post sparked a discussion (has comments)
- There's room to add a unique perspective with specifics

#### Strategy: ICP (potential customers)

Search for posts by people who:
- Work in ICP industries (Consumer Software, Fintech B2C, Consumer Services, etc.)
- Role: Head of Growth, VP Marketing, CMO, Performance Marketing Lead
- Write about: attribution challenges, marketing automation, scaling paid channels, LTV optimization
- Ad budget: $50K+/month (inferred from company scale)

**Do NOT sell in comments!** The goal is to become a visible expert, not to pitch.

#### Strategy: Networking (thought leaders)

Search for posts from:
- Industry thought leaders in performance marketing, MarTech, AI
- Podcast hosts and event organizers in our niche
- Founders of companies with similar missions
- Journalists and analysts covering MarTech / AI

### Step 3: Recommendations

For each recommended post / post type:

```markdown
### Target [N]

**Who to look for:** [profile description / type of content]
**Topics:** [keywords for search]
**Strategy:** [topic / icp / networking]
**Why:** [how it connects to the author's DIP]
**Possible angle:** [what specifics from the DIP can be added]
**Sample comment:** [1–2 sentence sketch]
```

### Step 4: Engagement Plan

```markdown
## Engagement Plan for [Author]

### Daily routine (recommended)
- 5–10 comments per day
- Mix: 30% team, 70% external
- Timing: before and after publishing your own post

### Distribution across strategies
- Topic (expertise): 40% — reinforces the profile in the niche
- ICP (customers): 30% — visibility with the target audience
- Networking (leaders): 30% — connections with industry leaders

### Key topics for this week
(based on Current-Trends + Algorithm-Intelligence)
1. [topic 1] — why it's relevant now
2. [topic 2] — why it's relevant now
3. [topic 3] — why it's relevant now
```

## Output

1. **List of recommended post types** with search criteria
2. **Engagement Plan** with strategy distribution
3. **Key topics of the week** for commenting
4. **Sample angles** for each target type

## Important

- This skill does NOT log into LinkedIn. It builds strategy and search criteria.
- The user finds concrete posts themselves and can use `/comment-on-post` to write a comment.
- Refresh recommendations weekly (via `/weekly-update`).
