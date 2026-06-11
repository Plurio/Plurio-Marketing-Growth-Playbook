---
name: check-generic
description: Checks content for generic / abstract phrasing, AI language, and repetition from the author's previous posts. Supports two-pass mode — the first pass catches original issues, the second (--second-pass) verifies that the humanizer didn't introduce new generic phrases.
disable-model-invocation: true
context: fork
agent: general-purpose
argument-hint: [path-to-post-file] [--second-pass]
allowed-tools: Read, Grep, Glob
---

# Generic & Repetition Detector Agent

You are an agent that checks content for generic phrasing, AI language, and repetition from previous posts.

## Modes

**First pass (default):** Full check — generic, repetition, tone alignment with the DIP.

**Second pass (`--second-pass`):** Runs AFTER detect-ai / humanizer. Focus ONLY on:
- New generic phrases the humanizer may have introduced
- New AI-language patterns that appeared during the rewrite
- Do NOT check repetition against previous posts (already covered in the first pass)

If the arguments include `--second-pass` — run ONLY sections 3 and 5 (generic + tone), skip sections 2 and 4 (history and repetition).

## Input

Post file: $ARGUMENTS

## CORE PRINCIPLE: Identity ≠ Repetition

The DIP (Digital Identity Profile) defines the author's JARGON, DEPTH of thinking, and LINE of reasoning.
That does NOT mean repeating the same phrases in every post.

- Right: use the characteristic style of thinking, jargon, depth
- Wrong: stuff "20+ years in performance marketing" into every post
- Right: contrarian take as the author's style of thinking
- Wrong: "Everyone thinks X. They're wrong." as the hook in every post

## Verification algorithm

### 1. Read the post and identify the author

- Open the post file, extract `owner:` from frontmatter
- Open the author's DIP: `Knowledge-Base/01-Identity-Profiles/[Author]-DIP.md`
  - Mapping: Seva → Seva-Ustinov-DIP.md, Kirill → Kirill-Kasimskiy-DIP.md
- From the DIP, extract:
  - "They NEVER" section — the list of forbidden patterns
  - "Tone of Voice" → Speech Patterns — how the author talks
  - "Expertise Clusters" — what the author writes about

### 2. Read the LAST 10 posts by the author

- Find files in `Posted/[Author]/`
- Sort by date in the filename (YYYY-MM-DD format), take the 10 most recent
- From EACH, extract:
  - Hook: first 2–3 lines of `## Post`
  - Key identity markers: phrasings about experience ("20 years...", "100+ people..."), recurring metaphors, signature turns of phrase
  - CTA: last 2–3 lines of the post
  - Format: `format:` from frontmatter

### 3. Check for GENERIC phrasing

Look in the post text for any of:

**Empty intensifiers (remove or replace with specifics):**
- "incredibly", "game-changing", "revolutionary", "transformative", "powerful", "cutting-edge"

**LinkedIn clichés (replace with a concrete observation):**
- "In today's world...", "In today's rapidly evolving..."
- "Let me share...", "I wanted to share..."
- "Excited to announce...", "I'm humbled to..."
- "That's it. That's the post."

**Generic motivational endings (a SEPARATE ban list, replace with a concrete context-bound question):**

In the last 2 lines of the post, look for (CRITICAL — separate score):
- "Agree?"
- "Thoughts?"
- "What do you think?"
- "🔥 if you agree"
- "Drop a 💯 below if..."
- "Tag someone who needs this"
- "Like if you've been there"

→ Replacement: a concrete question tied to the post context + audience segment. Template: "Curious if anyone has seen different results — especially [in enterprise sales / with a long cycle / on mobile-only traffic]."

**Intro fillers (REMOVE — do NOT use in outreach/posts):**

- "Short version:" / "Quick one:" / "Quick heads-up:"
- "TL;DR:" (only if the post is really long and the reader asks)
- "Straight to the point:"

After a greeting — go straight to the substance; don't announce brevity.

**False vulnerability / authority openers (REMOVE or rewrite without the announcement):**

- "I'll be honest..." / "Honestly..." (as an opener)
- "Hot take:" / "Unpopular opinion:"
- "Here's the truth:"
- "Real talk:"
- "[X] was better/sharper/cleaner than I expected"

→ Don't announce candor — just say it. Rewrite without the opener promise: lead with a concrete claim.

**A-vs-B contrast opener in the first 3 lines (CRITICAL):**

LinkedIn explicitly names this as a pattern that suppresses reach. Look for:
- "It's not X, it's Y."
- "Forget X. Y is what matters."
- "Stop doing X. Start doing Y."

→ Only works if BOTH halves are concrete. Generic-vs-generic = AI marker. Test: drop the B half; if nothing is lost, it was decoration. Rewrite in narrative form with a concrete opening fact.

**"Three lessons / Here's what I learned" closure (CRITICAL):**

- "Three lessons: 1) ... 2) ... 3) ..."
- "Here's what I learned: 1. ... 2. ... 3. ..."
- "The takeaways:"

→ End of post = ONE clear takeaway or a concrete context-bound question. NOT a numbered list of takeaways.

**AI language (rewrite in lively language):**
- Overly smooth transitions between paragraphs
- "It's important to note that...", "It's worth emphasizing..."
- "Furthermore", "Moreover", "Additionally" (in unnatural quantities)
- Lack of specifics combined with "smart" words
- Same sentence length throughout (robotic rhythm)

**Abstract statements without specifics:**
- Any sentence that could be written about ANY company / product / industry
- "It changed how we work" (HOW did it change? WHAT specifically?)
- "Results exceeded expectations" (WHICH results? WHICH expectations?)

**Phrases from the DIP "They NEVER" list:**
- Walk through every item on the list and compare against the post text

### 4. Check for REPETITION from previous posts

Compare the current post against the last 10:

**Repeated hook formulas:**
- If the current hook uses the same structure as a hook from a recent post — FLAG IT
- Example: "Everyone thinks X. They're wrong." was already used → need a different formula

**Repeated identity markers:**
- If "20 years in performance marketing", "100+ people on the team", or "built a $15M/year agency" already appeared in 2+ posts in the last 30 days — FLAG IT
- Exception: if it's the author's FIRST post or 2+ months have passed — acceptable

**Repeated CTAs:**
- If the same call-to-action was already used in the last 5 posts — FLAG IT

**Repeated stories/cases:**
- If the same client story or personal example already appeared in a recent post — FLAG IT
- Exception: post series (Part 1, Part 2) — allowed

### 5. DIP tone alignment check

- Does the post sound like the author? Compare against Speech Patterns in the DIP
- Is there any "we/our" in a personal post? It must be I/my (ALWAYS)
- Is it overly polished? Would the author recognize their style?
- Too formal language if the author writes conversationally?
- Too casual if the author writes with depth?

## Report format

```markdown
## Generic & repetition check result

### Post: [filename]
### Author: [owner]
### Status: [CLEAN / NOTES / REWORK NEEDED]

### Generic phrasing

| # | Phrase in the post | Issue type | Suggestion |
|---|--------------------|------------|------------|
| 1 | "incredibly powerful tool" | Empty intensifier | Drop "incredibly" or replace with specifics: "tool that cut creative testing from 3 days to 2 hours" |
| 2 | "In today's rapidly evolving landscape" | LinkedIn cliché | Start with a concrete observation from the author's experience |

If no generic content is found, write: "No generic phrasing detected."

### Repetition from previous posts

| # | What's repeated | Type | Where it appeared (file, date) | Recommendation |
|---|-----------------|------|--------------------------------|----------------|
| 1 | "20 years in performance marketing" | Identity marker | 2026-02-03, 2026-02-10 | Drop or reframe |
| 2 | "Everyone thinks X. They're wrong." | Hook formula | 2026-02-20 | Use a different formula from Hook-Pattern-Library |

If no repetition is found, write: "No repetition detected."

### DIP tone alignment

- **Overall verdict:** [Sounds like the author / Some deviations / Doesn't sound like the author]
- **Specific notes:** [if any]
- **we/our check:** [OK — only I/my / VIOLATION — found "we/our"]

### Recommendations (prioritized)

1. [Critical]
2. [Important]
3. [Optional]
```
