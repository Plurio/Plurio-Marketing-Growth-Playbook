---
name: suggest-next-post
description: Recommends what to write next. Analyzes the author's Topic Backlog, cluster balance, trends, and the algorithm. Prioritizes topics from Inbox into Prioritized. Helps avoid sameness and ride a trend.
disable-model-invocation: true
argument-hint: [Author]
allowed-tools: Read, Grep, Glob
---

# Suggest Next Post

What to write next? Prioritize topics from the Topic Backlog with cluster balance, trends, and the algorithm in mind.

## Input

- `$0` — author name (Seva, Kirill)

## Required files

1. **Author DIP:**
   `Knowledge-Base/01-Identity-Profiles/[Author]-DIP.md`
   → Expertise Clusters, cluster distribution, Viral Angles

2. **Topic Backlog:**
   `Posted/[Author]/Topic-Backlog.md`
   → Inbox topics, Prioritized, Done

3. **Posted (recent posts):**
   `Posted/[Author]/`
   → Last 10–15 posts for cluster and format analysis

4. **Algorithm-Intelligence:**
   `Knowledge-Base/02-LinkedIn-Algorithm/Algorithm-Intelligence.md`
   → Timing, formats, engagement rules

5. **Current-Trends:**
   `Knowledge-Base/03-Viral-Trends/Current-Trends.md`
   → What's trending now

6. **Format-Performance-Data:**
   `Knowledge-Base/02-LinkedIn-Algorithm/Format-Performance-Data.md`
   → Which formats perform better

## Pipeline

### Step 1: Current state analysis

#### 1A. Cluster balance

Read the author's last 10–15 posts. Extract `cluster:` from each frontmatter.

Compare actual distribution against the DIP target:

**Example:**

| Cluster | Target % | Actual % | Status |
|---------|----------|----------|--------|
| AI-Native Teams | 30% | 45% | OVER — reduce |
| Perf Marketing + Product | 30% | 20% | UNDER — add |
| Founder Journey | 20% | 25% | OK |
| Industry Insights | 20% | 10% | UNDER — add |

#### 1B. Format rotation

Last 5 posts → which formats were used?
If 3+ in a row in the same format → recommend a different one.

#### 1C. Timing

When was the last post? If >3 days ago — urgent.
Optimal frequency: 3–5 posts per week.

### Step 2: Topic Backlog analysis

Read the author's Topic-Backlog.md:
- **Inbox** — topics awaiting prioritization
- **Prioritized** — topics ready to write
- **Done** — already written

For each Inbox topic, score:

| Criterion | Weight | How to score |
|-----------|--------|--------------|
| Cluster fit | 30% | Needed cluster per balance → +3, over → −2 |
| Trend match | 25% | Matches Current-Trends → +3 |
| Unique angle | 20% | Has contrarian / fresh perspective → +2 |
| Source readiness | 15% | Raw source available (transcript, Telegram) → +2 |
| Urgency | 10% | Timely topic (event, news) → +3 |

### Step 3: Recommendations

```markdown
## What to write next — [Author]

### Date: [today]
### Last post: [date, topic]
### Cluster balance: [OK / skew toward X]

---

### Top 3 recommendations

#### 1. [Topic] ⭐ PRIORITY

**Cluster:** [cluster] — [why this cluster is needed now]
**Format:** [recommended format]
**Angle:** [from DIP Viral Angles]
**Source:** [which raw source to use]
**Trend match:** [match with Current-Trends]
**Score:** [N]/10

#### 2. [Topic]

[same fields]

#### 3. [Topic]

[same fields]

---

### Topics for Inbox → Prioritized

| Topic | Score | Cluster | Recommendation |
|-------|-------|---------|----------------|
| ... | N/10 | ... | Prioritized / Keep in Inbox / Remove |

### Cluster gap

**Need more posts on:** [cluster] — [specific topics from the DIP]
**Can wait:** [cluster] — [already well covered]
```

## Output

1. **Top 3 recommendations** with reasoning
2. **Inbox prioritization** — which topics to move into Prioritized
3. **Cluster gap** — where there's a shortfall
4. **Format recommendation** — what to use for the next post

## If the Topic Backlog is empty

Suggest topics from:
1. DIP Expertise Clusters — uncovered angles
2. Current-Trends — what's relevant now
3. Telegram scan — what landed on Telegram (suggest running `/scan-telegram`)
4. Transcripts — what came up in recent calls
