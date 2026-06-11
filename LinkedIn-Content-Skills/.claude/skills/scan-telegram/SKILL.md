---
name: scan-telegram
description: Scans the author's Telegram channel for content suitable for LinkedIn. Analyzes engagement (reactions, views), extracts topics, suggests repackaging. Telegram posts = valid raw source for the DIP and LinkedIn.
disable-model-invocation: true
argument-hint: [Author]
allowed-tools: Read, Grep, Glob
---

# Scan Telegram for LinkedIn Content

Scan the author's Telegram channel: engagement analysis → topic extraction → repackaging suggestions.

## Input

- `$0` — author name (Seva, Kirill)
- Optional: path to exported Telegram posts or a folder of files

## Required files

1. **Author DIP:**
   `Knowledge-Base/01-Identity-Profiles/[Author]-DIP.md`
   → Expertise Clusters, Topics, Tone of Voice

2. **Algorithm-Intelligence:**
   `Knowledge-Base/02-LinkedIn-Algorithm/Algorithm-Intelligence.md`
   → Which formats work on LinkedIn

3. **Current-Trends:**
   `Knowledge-Base/03-Viral-Trends/Current-Trends.md`
   → What's trending now

4. **Telegram source (per author):**
   `your-raw-sources/telegram-posts/`

5. **Posted (to check for duplicates):**
   `Posted/[Author]/`

## Why Telegram = a valuable source

- Telegram posts are written **personally by the author** (not AI-generated) → valid raw source
- Engagement (reactions, views) shows **what resonates** with the audience
- The Telegram style is closer to spoken speech → easier to preserve authentic voice
- Topic testing: what landed on Telegram has a high chance of landing on LinkedIn

## Pipeline

### Step 1: Find Telegram content

1. Identify the author → locate the folder with Telegram posts
2. Read all available posts
3. If there are no posts — tell the user, suggest exporting

### Step 2: Engagement Analysis

For each post, extract (if available):
- Views
- Reactions (likes, fire, etc.)
- Reposts
- Comments

Sort by engagement (high to low).

**Engagement Score** = reactions × 3 + comments × 5 + reposts × 10 (normalized by views)

### Step 3: Topic Extraction

For the top 20 posts by engagement:

1. **Identify the topic** — which Expertise Cluster from the DIP it belongs to
2. **Extract the key idea** — one sentence
3. **Assess LinkedIn potential:**
   - Has the topic already appeared on LinkedIn? (check Posted/)
   - Does it fit current trends? (Current-Trends)
   - Is there enough depth for a LinkedIn format?

### Step 4: Repackaging Suggestions

For each promising post:

```markdown
### Telegram → LinkedIn Opportunity [N]

**Telegram post:** [date, first 50 chars]
**Engagement:** [views / reactions / score]
**Topic:** [topic]
**DIP Cluster:** [cluster]
**LinkedIn potential:** HIGH / MEDIUM / LOW

**Why it fits LinkedIn:**
[1–2 sentences]

**Recommended format:**
[from Format-Catalog: story, contrarian take, how-to, etc.]

**Recommended angle:**
[from DIP Viral Angles]

**What the full post needs:**
- [what's already in the Telegram post]
- [what to add: specifics, numbers, case]

**Already on LinkedIn?**
[No / Yes — file, date]
```

### Step 5: Summary Report

```markdown
## Telegram Scan Report — [Author]

### Scan date: [today]
### Posts analyzed: [N]
### Top topics by engagement:

| # | Topic | Cluster | Engagement Score | LinkedIn potential | Already used? |
|---|-------|---------|------------------|--------------------|---------------|
| 1 | ... | ... | ... | HIGH/MED/LOW | No/Yes |

### Recommendations: what to write next

**Priority 1 (high engagement + not on LinkedIn yet):**
1. [topic] — [why now]

**Priority 2 (medium engagement, but trending):**
1. [topic] — [why now]

**Not recommended (already done or doesn't fit):**
1. [topic] — [why not]
```

## Important

- Telegram posts = INPUT (raw source). They're written personally by the author.
- LinkedIn posts = OUTPUT. Do NOT use LinkedIn posts as a source for new posts.
- When creating a post from Telegram content → cite Telegram as `source_ref`.
- Recommendations are added to the author's Topic Backlog: `Posted/[Author]/Topic-Backlog.md`
