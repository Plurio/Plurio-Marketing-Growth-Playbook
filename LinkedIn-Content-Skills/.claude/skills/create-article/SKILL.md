---
name: create-article
description: Creates a LinkedIn Article (long-form Pulse, 1000-2000 words) optimized simultaneously for AI-search (GEO) and the LinkedIn algorithm. Use when long-form content is needed with the goal of LLM citations. 8-step pipeline with a mandatory GEO checklist.
disable-model-invocation: true
argument-hint: [Author] [topic or LLM query]
allowed-tools: Read, Grep, Glob, Edit, Write, Skill(validate-content *)
---

# Create LinkedIn Article

> An Article is long-form pillar content (1,000–2,000 words) optimized for AI-search engines (ChatGPT, Perplexity, Google AI Overview) + the LinkedIn algorithm. Unlike a post, it has a permanent URL and gets indexed for LLM retrieval. One Article per week + 2–3 posts is the standard cadence.

## When to invoke

- The user says "write an Article", "write long-form", "do a Pulse"
- The topic is "big" — won't fit in a 1,200–1,800-character post, needs a framework / multiple H2s
- The topic is phrased as a **question** the audience would ask ChatGPT (classic GEO signal)
- You want long-tail discovery through LLM engines, not a one-shot engagement spike

## When NOT to invoke

- Topic is short, single insight = `/create-post` (LinkedIn post)
- Personal story / reflection without an actionable framework = `/create-post`
- Topic doesn't match the author's headline (Profile-Content Alignment gates reach)
- Author has already had this topic in an Article in the last 3 months — pick a different angle

## Pipeline (8 steps)

### Step 1: Load context

Read the mandatory items:

1. `Knowledge-Base/01-Identity-Profiles/[Author]-DIP.md` — voice, expertise clusters, viral angles
2. `Knowledge-Base/10-Articles-and-GEO/LinkedIn-Articles-GEO-Framework.md` — 6 GEO principles
3. `Knowledge-Base/02-LinkedIn-Algorithm/Algorithm-Intelligence.md` — LinkedIn algorithm
4. `Articles/Articles-Plan-Template.md` — structural template
5. `Hook-Bank.md` — for choosing the hook angle

Optional:

6. `Knowledge-Base/01-Identity-Profiles/_Voice-Vocabulary/[Author]-Voice-Vocabulary.md` (if it exists)
7. Recent posts from `Posted/[Author]/` (last 5) — to avoid repetition
8. Recent Articles from `Articles/Posted/[Author]/` (if any) — to avoid repetition

### Step 2: Phrase the title as an LLM query

The title must be the exact phrasing of the question a user would ask ChatGPT/Perplexity.

**Test:** type the title into Google. "People also ask" should surface a similar question.

Pattern examples:

- "How [does/do] X [verb] Y?" → "How AI Agents Manage Ad Budgets"
- "When to [action]: [framework]" → "When to Kill Underperforming Ads"
- "What Is [concept]? [Numbered framework]" → "What Is an AI-Native Company? 12 Steps"
- "Why [observation about industry] [+ counter-take]" → "Why Your CRM Is Missing 30–40% of Lead Sources"

### Step 3: Write the Lead Paragraph (direct answer)

The first 2–3 sentences = DIRECT ANSWER to the question in the title.

❌ "Let me set up the context. In today's marketing world..."
✅ "AI agents manage ad budgets by monitoring campaigns in real time, detecting anomalies before metrics shift, and either alerting humans or auto-adjusting within guardrails. In practice at $20M+ scale, this looks like..."

**This is the most important paragraph of the article.** The LLM will pull it as the summary.

### Step 4: Design 4–6 H2 sections

Structure pattern:

```text
H2: Why this matters / The problem
H2: What [your concept] actually does / The framework
H2: Real results / Real cases (with concrete numbers)
H2: How to start (even without [your product])
H2: Where most teams get stuck (optional)
```

Each H2 must work **standalone** (an LLM can extract one).

### Step 5: Create ONE unique concept with its own name

Every Article should have 1 named concept your audience can find.

Examples from practice:

- "Trust adoption curve" — chat → autonomous progression
- "5 levels of AI ad management" — numbered scale
- "The 30–40% CRM attribution gap" — statistic-as-phrasing

**Test:** is the phrasing unique? If others say the same — you need a new angle.

### Step 6: Pack with concrete numbers

Minimum 5 fact-rich points in the article:

- ❌ "AI saves time" → ✅ "Analysis that took 90 minutes now takes 10"
- ❌ "Most leads are tracked" → ✅ "30–40% of leads hit CRM with no source data"
- ❌ "We test creatives" → ✅ "We analyzed 1,180 creatives — optimal kill threshold isn't $5 or $100"

Numbers must come with **context**: what, at what scale, compared to what.

### Step 7: Internal GEO checklist

Before publication, walk the checklist:

- [ ] Title — is it a ChatGPT/Perplexity query?
- [ ] First paragraph **directly answers** the title question?
- [ ] H2 subheadings (minimum 4)?
- [ ] Each section works standalone?
- [ ] One named concept (unique formulation)?
- [ ] Minimum 5 concrete numbers with context?
- [ ] 1,000–2,000 words?
- [ ] Author headline and recent post topics align with the topic (Profile-Content Alignment)?
- [ ] Closing without a marketing CTA (lowers LLM-trust)?
- [ ] Links to own resources (if any) for backlink signal?

### Step 8: Save + automatic validation

Save to `Articles/Posted/[Author]/YYYY-MM-DD-[slug].md` with frontmatter:

```yaml
---
title: "[Title]"
author: [Author]
published_date: YYYY-MM-DD
publication: LinkedIn Pulse
direct_url: TBD
companion_post: TBD
named_concept: "[your unique concept name]"
geo_target_queries:
  - "[query 1 — branded]"
  - "[query 2 — topic]"
  - "[query 3 — mid-funnel]"
hook_bank_refs:
  - "#N"
sources:
  - "[transcript / podcast / call from which content derived]"
status: draft / published / audited
---
```

Then invoke `/validate-content [path] --type article` for:

- check-facts
- check-generic (no AI markers)
- check-sources (each claim → source)
- detect-ai

If everything is clean → ready for publication.

## Output

A file at `Articles/Posted/[Author]/YYYY-MM-DD-[slug].md` + alternative leads (3 variants) + timing recommendation + companion post draft (1,200–1,500 characters, teaser hook + link to the Article).

## Worked examples

See `Articles/_Examples/` in this repo — 5 published Articles that went through the full pipeline. Study them before running the skill for the first time.

## Post-publication

After 4 weeks — invoke `/audit-llm-visibility [article-path]` to check:

- Direct URL discoverability
- Content citation in AI summaries
- Brand share-of-voice on ICP queries

Results — in `Articles/_Audits/YYYY-MM-DD-[slug]-audit.md`.

## Anti-patterns

| Anti-pattern | Why it's bad |
|--------------|--------------|
| Clickbait title without substance | LLMs skip clickbait |
| Lead paragraph as intro-anecdote | Wastes the main slot |
| 2 articles per week from one author | LinkedIn cuts distribution (40% penalty) |
| Marketing CTA in conclusion | Lowers LLM-trust, citation rate falls |
| Topic doesn't match author headline | Profile-Content Alignment gates reach |
| Article = rewritten post | Wastes the Article cadence |
