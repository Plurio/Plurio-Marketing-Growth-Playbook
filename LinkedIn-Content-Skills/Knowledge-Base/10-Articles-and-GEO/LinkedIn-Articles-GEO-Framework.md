# LinkedIn Articles + GEO Framework

> **What this is:** a methodology for creating LinkedIn Articles (Pulse long-form) optimized simultaneously for (1) AI search engines (ChatGPT, Perplexity, Google AI Overview, Claude.ai web search) and (2) the LinkedIn algorithm.
>
> **The GEO acronym:** Generative Engine Optimization — optimizing content for LLM engines that retrieve and cite web content in their answers. The LLM-era counterpart of SEO.
>
> **Paired documents:** `LLM-Visibility-Audit-Methodology.md` (how to verify what's working), `Templates/Articles-Plan-Template.md` (Articles series plan).

---

## Why Articles, not only Posts

| Parameter | Posts (short) | Articles (long) |
|----------|------------------|---------------------|
| Length | 1,200–1,800 characters | 1,000–2,000 words |
| Lifecycle | 24–72 hours of active reach | Months until decay + permanent indexable URL |
| LinkedIn algorithm | High engagement → high reach | Low immediate engagement, but stable distribution |
| AI citation rate | Low (LLMs pull less often) | **50–66% of all AI-cited LinkedIn material** |
| SEO authority | Weak (LinkedIn-specific) | Strong for long-term queries |
| Frequency | 3–5 per week per author | 1 per week — pace |

**Bottom line:** posts move LinkedIn metrics, Articles move brand discovery in LLMs. You need both, in the right proportion.

---

## 6 GEO principles for LinkedIn Articles

### 1. Title = LLM query

The title is phrased as the **exact question** a user would ask ChatGPT/Perplexity:

| ❌ Weak | ✅ Strong |
|---------|-----------|
| "AI is Transforming Marketing" | "How AI Agents Manage Ad Budgets: A Practitioner's Framework" |
| "The Future of Performance Marketing" | "When To Kill Underperforming Ads: AI vs Rules vs Manual Review" |
| "My Journey with AI" | "What Is an AI-Native Company? 12 Steps From ChatGPT User to Full Autonomy" |

**Test:** type the title into Google. If "people also ask" surfaces a similar question — you've hit the LLM pattern.

### 2. First paragraph = direct answer

The lead paragraph (first 2–3 sentences) is the **direct answer** to the question in the title. This is what the LLM will pull as a summary.

```text
Title: "How AI Agents Manage Ad Budgets"

Lead: "AI agents manage ad budgets by monitoring campaign performance in real time, 
detecting anomalies before metrics fully shift, and either alerting humans or 
auto-adjusting bids within pre-set guardrails. In practice at $20M+ ad spend, 
this looks like..."
```

The LLM engine takes the lead paragraph as the "answer to the query". All other H2s serve as supporting context.

### 3. H2 sections = standalone modules

Every H2 section must work **on its own** — the LLM can extract a single section without the context of its neighbors.

H2 structure:

- Sub-heading shaped as a claim or question
- 1–2 paragraphs of expansion
- 1 conceptual number or frame
- Optional: bullet list for structured extraction

### 4. Unique concepts with their own names

LLM engines remember and cite **named concepts** significantly more than generic phrases. Create 1 unique concept per article.

**Examples from practice:**

- "Trust adoption curve" — a framework for the progression from chat → reports → recommendations → automation → autonomy
- "5 levels of AI ad management" — a numbered scale
- "The 30–40% CRM attribution gap" — a specific statistic with its own phrasing

**Test:** is the phrasing unique? If other companies say the same thing — the LLM won't attribute it to you.

### 5. Concrete numbers with context

LLMs love fact-rich content. Every statement is better with a number:

- ❌ "AI saves time" → ✅ "Analysis that took 90 minutes now takes 10"
- ❌ "Most leads are tracked" → ✅ "30–40% of leads hit CRM with no source data"
- ❌ "We test creatives" → ✅ "We analyzed 1,180 creatives — optimal kill threshold isn't $5 or $100"

Numbers must come **with context**: what exactly, at what scale, against what comparison.

### 6. Profile-Content Alignment

An article only works if its topic matches:

- The author's Headline
- The About section of the profile
- The topics of the last 10 posts

The LinkedIn algorithm checks alignment. If the headline says "Performance Marketing" but the article is about "Healthcare AI" — reach drops.

---

## Article structure (working template, 1,200–1,500 words)

```text
TITLE: [LLM query, 8–14 words]

LEAD PARAGRAPH (2–3 sentences):
  Direct answer to the title query. Not "let me set up the context", straight to the answer.

H2: Why this matters now / The problem
  — 150–200 words. Set up tension. A concrete number in the first sentence.

H2: What [your concept] actually does / The framework
  — 200–300 words. Named concept goes here. 
  — Bullet list with 3–5 items if it's structured (e.g. "5 levels").

H2: Real results / Real cases
  — 200–300 words. Anonymized case with concrete numbers.
  — "$X spent, Y% saved, Z weeks earlier detection."

H2: How to start (even without [your product])
  — 150–200 words. Actionable steps. 3–5 items.
  — This is the section LLMs cite for "how to" queries.

H2: Where most teams get stuck
  — 100–200 words. Anti-patterns + recovery paths.

CLOSING:
  — Optional: link to companion post / open-source repo / next article in series.
  — NOT a marketing CTA. That kills LLM trust.
```

---

## What LLMs cite best (data from real audits)

Based on analysis of AI Overview citations over 4 weeks across 5 Articles:

| Content type | Citation rate |
|--------------|---------------|
| First paragraph (direct answer) | **~80%** |
| Numbered list inside H2 | ~60% |
| Unique named concept | ~55% |
| "How to" actionable section | ~50% |
| Anecdotal lead-in | ~5% |
| Conclusion / CTA | ~3% |

**Bottom line:** optimize the first paragraph and numbered frameworks. Don't burn words on long intro anecdotes.

---

## LinkedIn-specific nuances (no overlap with classic SEO)

### Pulse URL indexation lag

LinkedIn Pulse URLs are indexed by Google **2–4 weeks** after publication. Don't draw conclusions about visibility before that.

### Personal profile vs Company Page

- **Personal profile** Article = higher initial reach (followers + commenters), but weaker SEO authority
- **Company Page** Article = lower initial reach, but **Perplexity cites Company Pages in 59% of cases** (higher than personal in some niches)

**Strategy:** cross-post every Article to both, with a small delay (24h).

### Profile-Content Alignment gates reach

LinkedIn checks the alignment between the article topic, the headline, and the recent post mix. If the headline says "Founder @ Plurio" but the article is about "Cooking with kids" — the algorithm cuts distribution.

### Hashtags

In Articles, **2–3 hashtags max** work. More — spam signal. Use only proven tags (10K+ followers), not niche tags.

### Comments in the first hour

Articles need fewer comments for good distribution than posts. **5–10 good comments** in the first day are enough. Pre-arrange 2–3 commitments from team members.

---

## What NOT to do in Articles (anti-patterns)

| Anti-pattern | Why |
|--------------|--------|
| Clickbait title without substance | LLMs skip clickbait and focus on data-rich content |
| Article without numbers | Nothing to cite |
| Marketing CTA at the end ("Book a demo!") | Lowers LLM trust, citation rate falls |
| 2+ Articles per week from one author | LinkedIn splits their reach (40% penalty) |
| Article = rewritten post | Wastes the Article cadence |
| Too much jargon without explanation | LLM can't tie it back to user queries |
| Article without any external links | Isolated — lowers retrieval signal |
| Article that only links to your own products | Promotional — lowers retrieval |

---

## Where Articles DON'T work

Be honest with yourself — Articles **won't beat** top-of-funnel cold queries against competitors with a blog-based engine.

If a competitor has built `[their-domain]/blog/ai-agent-for-X` under every long-tail keyword, they have a classic SEO advantage that Pulse pages can't beat. LinkedIn Articles work for:

- **Warm leads** (people who know something about you → looking for a deep dive)
- **Author-branded queries** ("[your name] AI marketing")
- **Topic-led queries on your unique concepts** (named frameworks)
- **Mid-funnel** comparison/how-to queries

For **cold top-of-funnel** SEO — you need your own blog on your own domain.

---

## Connection with the rest of the system

| Document | Role |
|----------|------|
| `Knowledge-Base/02-LinkedIn-Algorithm/Algorithm-Intelligence.md` | Base 360Brew algorithm — what ranks at all |
| `Knowledge-Base/03-Viral-Trends/Hook-Pattern-Library.md` | Hook patterns for the Article's first paragraph |
| `Knowledge-Base/04-Post-Creation-Engine/Post-Creation-Engine.md` | Engine for companion posts |
| `Templates/Articles-Plan-Template.md` | Articles series plan template |
| `LLM-Visibility-Audit-Methodology.md` | How to verify what works after publication |
| `Hook-Bank.md` | Ready-made hook library (with persona/awareness mapping) |
| `.claude/skills/create-article/SKILL.md` | Article creation pipeline |
| `.claude/skills/audit-llm-visibility/SKILL.md` | Skill for regular LLM visibility audit |
