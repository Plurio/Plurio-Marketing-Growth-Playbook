---
name: weekly-update
description: Weekly refresh of the LinkedIn Content Machine. Algorithm refresh + content scan + performance review + trend update. Run once a week to keep the system current.
disable-model-invocation: true
argument-hint: (no arguments needed)
allowed-tools: Read, Grep, Glob, Agent
---

# Weekly Update — LinkedIn Content Machine

Weekly refresh of the whole system: algorithm, trends, performance, content plan.

## When to run

- Once a week (Monday morning is ideal)
- After meaningful changes to the LinkedIn algorithm
- On user request

## Required files

1. **Weekly-Update-Workflow:**
   `Knowledge-Base/07-Auto-Update/Weekly-Update-Workflow.md`

2. **Algorithm-Intelligence:**
   `Knowledge-Base/02-LinkedIn-Algorithm/Algorithm-Intelligence.md`

3. **Current-Trends:**
   `Knowledge-Base/03-Viral-Trends/Current-Trends.md`

4. **Performance-Log:**
   `Knowledge-Base/05-Format-Testing/Performance-Log.md`

5. **Posted (all authors):**
   `Posted/*/`

## Pipeline

### Step 1: Performance Review (30 min)

For EACH active author (active authors):

1. Read this week's posts from `Posted/[Author]/`
2. If there are metrics in Performance-Log → extract and analyze
3. Identify:
   - Best post of the week (by engagement)
   - Worst post of the week
   - Average engagement
   - Trend: rising / falling / stable

### Step 2: Content Audit (20 min)

For each author:
1. Count this week's posts
2. Check cluster balance (last 10 posts vs DIP target)
3. Check format rotation (last 5 posts)
4. Check for gaps (didn't publish for 3+ days?)

### Step 3: Algorithm & Trends Scan (20 min)

1. Check `Algorithm-Intelligence.md` — do any updates need to happen?
2. Check `Current-Trends.md` — are the trends still current?
3. If there's new data → update the files

### Step 4: Topic Backlog Review (15 min)

For each author:
1. Read `Posted/[Author]/Topic-Backlog.md`
2. Move published topics from Prioritized to Done
3. Check: is there anything in Prioritized for next week?
4. If Prioritized is empty → suggest running `/suggest-next-post`

### Step 5: DIP Health Check (10 min)

For each author:
1. Check the DIP version (v0.5 → needs an upgrade)
2. Check the Feedback Log — is there unrecorded feedback?
3. If 5+ posts have passed since the last DIP update → recommend `/update-dip`

### Step 6: Weekly Report

```markdown
## Weekly Update — LinkedIn Content Machine

### Week: [start date] — [end date]
### Update date: [today]

---

### Performance Summary

| Author | Posts this week | Best post | Engagement trend |
|--------|------------------|-----------|------------------|
| Seva | [N] | [slug] | ↑ / → / ↓ |
| Kirill | [N] | [slug] | ↑ / → / ↓ |
| Ella | [N] | [slug] | ↑ / → / ↓ |
| Denis | [N] | [slug] | ↑ / → / ↓ |

---

### Content Audit

| Author | Cluster balance | Format rotation | Gaps |
|--------|------------------|------------------|------|
| Seva | OK / skew toward [X] | OK / repeat [X] | None / [N] days |
| ... | ... | ... | ... |

---

### Algorithm & Trends

**Updates to Algorithm-Intelligence:** [yes / no]
**Updates to Current-Trends:** [yes / no]
**Key changes:** [if any]

---

### Topic Backlog Status

| Author | Inbox | Prioritized | Done (this week) | Needs replenishing? |
|--------|-------|-------------|------------------|---------------------|
| Seva | [N] | [N] | [N] | Yes / No |
| ... | ... | ... | ... | ... |

---

### DIP Health

| Author | Version | Posts since last update | Recommendation |
|--------|---------|-------------------------|----------------|
| Seva | v1.0 | [N] | OK / Needs update |
| ... | ... | ... | ... |

---

### Action items for next week

**Critical:**
1. [...]

**Recommended:**
1. [...]

**Optional:**
1. [...]
```

## What gets auto-updated

- Performance-Log.md (if new metrics are available)
- Topic-Backlog.md (move Done)
- Algorithm-Intelligence.md (if new data exists)
- Current-Trends.md (if new trends emerged)

## Relation to other skills

- `/suggest-next-post` — if the Topic Backlog is empty
- `/scan-telegram` — if new topics are needed
- `/update-dip` — if the DIP is outdated
- `/find-comment-targets` — for the engagement strategy for the week
