---
name: post-publication
description: Golden window workflow — the first 90 minutes after publishing a LinkedIn post. Checklist of actions to maximize reach: replying to comments, engagement routine, sharing strategy. Critical for the algorithm.
disable-model-invocation: true
argument-hint: [Author] [post-file-path]
allowed-tools: Read, Grep, Glob
---

# Post-Publication Golden Window

Workflow for the first 90 minutes after publishing a LinkedIn post. Maximizing reach through strategic engagement.

## Input

- `$0` — author name (Seva, Kirill)
- Optional: path to the post file

## Required files

1. **Author DIP:**
   `Knowledge-Base/01-Identity-Profiles/[Author]-DIP.md`

2. **Comments-Engine:**
   `Knowledge-Base/06-Comments-Engine/Comments-Engine.md`

3. **Algorithm-Intelligence:**
   `Knowledge-Base/02-LinkedIn-Algorithm/Algorithm-Intelligence.md`

## Why the Golden Window is critical

| Fact | Source |
|------|--------|
| The first 60–90 minutes determine the post's reach | Algorithm-Intelligence (360Brew model) |
| Author reply within the first 30 min → +64% total comments, 2.3× views | Richard van der Blom |
| Commenting on 5–10 posts after publication → +55% profile views | Algorithm-Intelligence |
| Dwell time in the first hour → quality signal for the algorithm | 360Brew |
| Author's first comment in the first 5 min → steers the discussion | Comments-Engine |

## Timeline

### T+0 min: Publication

- [ ] Post published
- [ ] Author's first comment ready (Type 3: discussion starter)

### T+0–5 min: First comment

Publish the pre-prepared first comment (from `/create-post` output):
- Bonus insight, or
- Guiding question, or
- Behind the scenes

**Rules:**
- Do NOT repeat the post's content
- Do NOT include links (penalized as of 2026)
- 15+ words

### T+5–15 min: Cross-team amplification

Teammates leave their own comments:

| Who | Angle | Timing |
|-----|-------|--------|
| Teammate 1 | Their own unique angle (doesn't repeat the author) | T+5–10 min |
| Teammate 2 | Different angle | T+10–15 min |

**Rules:**
- Each teammate = unique angle
- Do NOT overlap with other comments
- 30% team, 70% external (overall balance)

### T+15–30 min: Engagement routine

The author comments on 5–10 posts in their niche:
- ICP-audience posts
- Posts by thought leaders
- Posts on topics from Expertise Clusters

**Why:** the algorithm sees profile activity → more reach for the post you just published.

### T+30–60 min: Replies to comments

- Reply to EVERY comment
- Minimum 15 words for substantive replies
- Vary the phrasing (no single formula)
- Ask follow-up questions (drives the thread)

Use `/reply-to-comments [Author]` to generate replies.

### T+60–90 min: Second engagement round

- Another 3–5 comments on others' posts
- Check new comments under your post → reply
- If DM requests came in → reply

### T+90+ min: Monitoring

- Check comments every 2–3 hours during the day
- Reply to all new comments
- Do NOT publish a new post within 12 hours

## Sharing Strategy

### Internal distribution

| Channel | Action | Timing |
|---------|--------|--------|
| Team (Slack/Telegram) | Share the link + ask for engagement | T+0 |
| Partners | DM with the link (if relevant) | T+30 min |

### External distribution

| Channel | Action | Timing |
|---------|--------|--------|
| Author's Telegram channel | Cross-post with adaptation | T+60 min |
| Email newsletter (if any) | Include in the next issue | Next issue |

## Output: Post-Publication Checklist

```markdown
## Post-Publication Checklist — [Author]

### Post: [title / slug]
### Published: [date, time]

### Ready materials

**Author's first comment:**
[text]

**Teammate 1 comment ([name]):**
[text]

**Teammate 2 comment ([name]):**
[text]

### Timeline

- [ ] T+0: Post published
- [ ] T+0–5: Author's first comment
- [ ] T+5–15: Teammate comments
- [ ] T+15–30: Engagement routine (5–10 posts)
- [ ] T+30–60: Replies to comments
- [ ] T+60–90: Second engagement round
- [ ] T+90+: Monitor every 2–3 hours

### Engagement targets for commenting

1. [post type / topic] — [angle]
2. [post type / topic] — [angle]
3. [post type / topic] — [angle]

### Distribution

- [ ] Team notified
- [ ] Telegram cross-post (T+60)
- [ ] Partners (if relevant)
```

## Relation to other skills

- `/create-post` → generates post + first comment + cross-team comments
- `/reply-to-comments` → generates comment replies in batch mode
- `/find-comment-targets` → recommends posts for the engagement routine
- `/comment-on-post` → writes individual comments on identified posts
