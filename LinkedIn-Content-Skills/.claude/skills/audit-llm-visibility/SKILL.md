---
name: audit-llm-visibility
description: Checks whether an author's LinkedIn Article(s) are cited by LLM engines (ChatGPT, Perplexity, Google AI Overview, Claude.ai web). Runs a list of ICP queries, records citations, and computes share-of-voice. Run 4+ weeks after publishing an Article.
disable-model-invocation: true
argument-hint: [article-path] [--full | --queries-only]
allowed-tools: Read, Grep, Glob, Write, WebFetch, WebSearch
---

# Audit LLM Visibility

> This audit checks whether your content is being cited by LLM engines on queries relevant to your target audience. It's the GEO equivalent of Google Search Console for SEO.

## When to invoke

- **4+ weeks** after publishing an Article (earlier than that — indexation lag, nothing should have kicked in yet)
- **Quarterly** — full audit across all published Articles
- Before planning the next Articles series — to understand which patterns are working

## When NOT to invoke

- Right after publication (too early to judge)
- For short posts (LLMs rarely cite short-form)
- Without a list of ICP queries (you need specific target queries, not generic ones)

## Pre-requisites

Before running, you need:

1. Article(s) published 4+ weeks ago
2. Direct Pulse article URL saved in frontmatter
3. `geo_target_queries` written in frontmatter (minimum 5 queries)
4. Published on the personal profile (optionally — on the Company Page)

## Pipeline (5 steps)

### Step 1: Load context

1. Read `Knowledge-Base/10-Articles-and-GEO/LLM-Visibility-Audit-Methodology.md` — methodology
2. Read the target article — find `direct_url`, `geo_target_queries`, `named_concept`
3. If running in `--full` mode — read the competitor list from `Knowledge-Base/03-Viral-Trends/Viral-Trends-Watchlist.md` (for share-of-voice tracking)

### Step 2: Prepare query list

Take `geo_target_queries` from the article frontmatter. Expand to **minimum 20 queries** covering 4 categories:

| Category | Count | Source |
|----------|-------|--------|
| A. Branded ("[Company] reviews") | 5 | From frontmatter |
| B. Author-branded ("[Author] [topic]") | 3 | From frontmatter |
| C. Topic + named concept | 5 | From frontmatter (named_concept) |
| D. Generic ICP top-of-funnel | 5 | From frontmatter |
| E. Comparative ("[Your product] vs X") | 2 | From Viral-Trends-Watchlist |

If frontmatter doesn't have enough — ask the user.

### Step 3: Run queries through LLM engines

**For each query** — perform web searches and record results:

1. **WebSearch:** query → check whether your Article shows up in results
2. **WebFetch for AI Overview:** `https://www.google.com/search?q=[query]` → check AI Overview section
3. **Optional:** if API access is available — Perplexity API, ChatGPT API with browsing

For each result, record:

- Does your brand appear?
- Which URL is cited (if any)?
- Verbatim quotes from your article (exact match)?
- Which competitors are mentioned?
- Tone of mention (positive / neutral / context-only)

### Step 4: Analyze results

Group findings by category. Compute:

```text
Citation rate (per category) = N queries with brand mention / total queries
Direct URL discovery rate    = N queries where Article URL appears / total
Verbatim citation rate       = N queries with direct quote / total
Competitor share-of-voice    = competitor mentions / total mentions
```

Apply decision rules from `LLM-Visibility-Audit-Methodology.md`:

- Categories A+B+C work, D+E don't → normal for LinkedIn-only. Continue.
- No category works after 4 weeks → problem in Article structure. Recommend revision.
- Competitors dominate D+E → confirms you need your own blog with SEO for cold acquisition.

### Step 5: Save audit report

Create file `Articles/_Audits/YYYY-MM-DD-[article-slug]-audit.md` using the template from `LLM-Visibility-Audit-Methodology.md` ("Audit report template" section):

```markdown
# LLM Visibility Audit — [Date] — [Article slug]

> **Article:** [title]
> **Age:** [days since publish]
> **Method:** [manual / WebSearch + WebFetch]

## TL;DR — 3 key findings

1. ...
2. ...
3. ...

## Per-category results

[5 categories with metrics + examples]

## Verbatim citations found

[list of direct quotes from Google AI Overview / other engines]

## Verdict: [X/10]

[1-line summary]

## Recommendations

[3–5 action items with owner + deadline]
```

## Output

1. **Report file** in `Articles/_Audits/`
2. **Inline chat summary** — TL;DR + verdict
3. **Suggested next actions** — what to improve in article structure, which queries to add in the next monitoring round

## What this skill does NOT do

- Does NOT predict future visibility (only current state)
- Does NOT auto-optimize the article (only shows where it fails)
- Does NOT track competitor mentions in historical view (need `--full` mode for baseline)
- Does NOT replace professional AEO-tracking tools at scale (Profound, Athena AI, Otterly.AI) — this is manual baseline + early warning

## Anti-patterns

- ❌ Running 1 week after publication (too early)
- ❌ Only Category A (creates illusion of visibility)
- ❌ Only one LLM engine (need at least 2 for reliability)
- ❌ Audit without action items (becomes a shelf document)
- ❌ Running more often than every 2 weeks (changes don't surface that fast)

## Relation to the system

| Document | How it relates |
|----------|----------------|
| `LinkedIn-Articles-GEO-Framework.md` | What an article needs to have to pass this audit |
| `Articles-Plan-Template.md` | Where to write `geo_target_queries` in advance |
| `Growth-Loop-Architecture.md` | LLM citation rate can be added as a metric in the Growth Loop |
| `.claude/skills/create-article/SKILL.md` | Creates the article with the frontmatter this skill reads |
