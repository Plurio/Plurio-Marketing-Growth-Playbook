# LLM Visibility Audit — Methodology

> **What this is:** a methodology for checking whether your content is being cited by LLM engines (ChatGPT, Perplexity, Google AI Overview, Claude.ai web search, Bing Copilot) on queries from your target audience.
>
> **When to run it:** every 4 weeks after publishing an Article (earlier than that — indexing won't have caught up). Full audit — once a quarter.
>
> **Paired document:** `LinkedIn-Articles-GEO-Framework.md` — the methodology for creating GEO-optimized content itself.

---

## What we measure (3 metrics)

### 1. Direct URL discoverability

Can the exact URL of your Article be found through search queries?

**Test query format:**

```text
site:linkedin.com/pulse "[exact title phrase]"
site:linkedin.com/pulse "[your name]" "[unique concept]"
"[article title]" linkedin
```

**What it means:**

- ✅ URL in Top 5 → Google index is working
- ⚠️ URL in Top 20 → indexed, but weak authority
- ❌ Not found → indexation lag or penalty (new Pulse URLs may take 2–4 weeks to index)

### 2. Content citation in AI summaries

Are LLM engines citing phrasings from your Article in answers to topic queries?

**What to look for:**

- Direct quotes (exact phrases) from your Article
- Paraphrases with attribution to you ("[Your name] from [Company] wrote about...")
- Paraphrases WITHOUT attribution (citation without credit — worth monitoring separately)

**This is the main signal.** If LLMs cite you on topic queries — GEO is working.

### 3. Brand share-of-voice on ICP queries

On what percentage of your ICP queries do you show up in the results?

**Calculation:** out of a list of X ICP queries, you are mentioned in N% (in any form — link, citation, name-drop).

---

## 4 categories of test queries

A balanced audit covers all 4 categories.

| Category | Goal | Query format | Example |
|-----------|------|----------------|--------|
| **A. Branded** | Knows you, looking for reviews | "[Company] reviews / alternatives / vs [Competitor]" | "Plurio AI agent reviews" |
| **B. Author-branded** | Knows a specific author | "[Author name] [topic]" | "Seva Ustinov LinkedIn AI agents" |
| **C. Topic + concept** | A unique concept from your article | "[your named framework]" | "Trust adoption curve AI agent" |
| **D. Generic ICP top-of-funnel** | Cold potential customer | "Best [category] for [use case] 2026" | "Best AI agent for performance marketing 2026" |

**Pattern from real audits:**

- Categories A and B: **usually work** with 4+ weeks of content
- Category C: **works if the concept is unique** (you are the only source in the LLM index)
- Category D: **usually does NOT work** for a LinkedIn-only strategy — you need your own blog with SEO

---

## Query list for regular monitoring

> Minimum: 20 queries once a month. Optimal: 30 queries every 2 weeks + a competitor tracker.

### Category A: Branded (awareness)

1. "What is [your product]?"
2. "[Your product] vs [Top competitor 1]"
3. "[Your product] reviews"
4. "[Your product] pricing"
5. "[Your product] alternatives"

### Category B: Author-branded

6. "Who is [Your author name]?"
7. "[Your author name] [your topic vertical]"
8. "[Co-author name] [their specialty]"

### Category C: Topic-led (concepts from your articles)

9. "[Your unique framework name] [domain]"
10. "[Your named formula]"
11. "[Your concept 1]"
12. "[Your concept 2]"
13. "[Open-source project name if any]"

### Category D: Mid-funnel ICP

14. "How does [your category] work?"
15. "When to [your problem space action]"
16. "[Your category] for [specific persona]"
17. "How to [your problem space action]"
18. "Why does [your problem signal] happen"
19. "How to fix [your problem area]"

### Category E: Top-of-funnel (cold)

20. "Best [your category] [current year]"
21. "Best [adjacent category] tools [current year]"
22. "[Your category] AI [current year]"
23. "How to automate [your problem space]"
24. "Best alternative to [dominant competitor]"
25. "[Your category] AI [current year]"

### Category F: Comparative

26. "[Your product] vs [Competitor 2]"
27. "[Your product] vs [Competitor 3]"
28. "[Top competitor] alternatives"
29. "Best [problem] tools"
30. "AI [your space] vs traditional"

---

## How to run it (manual baseline → automation)

### Tier 1: Manual run (free, 1–2 hours)

1. Open 4 LLM engines in your browser:
    - ChatGPT (web, with browsing)
    - Perplexity
    - Claude.ai (with web search)
    - Google (for AI Overview)
2. Run the list of 20–30 queries in each engine
3. For each answer, record:
    - Does your brand appear?
    - Which URL was cited (if any)?
    - Which competitors are mentioned?
    - Tone of mention (positive / neutral / mention without context)

**Save to:** a Google Sheet with columns [Query | Engine | Brand mentioned? | URL cited | Competitors | Notes].

### Tier 2: Semi-automated ($30–100/month)

1. Script via OpenAI API + Perplexity API + Anthropic API + custom Google Search wrapper
2. Runs the query list once a week
3. Parses the answers → calculates share-of-voice → loads it into a dashboard

**Tools:** Python + requests, minimal schema, $30–100/month at moderate volume.

### Tier 3: Professional (~$300+/month)

Professional AEO tracking platforms:

- **Profound** — specializes in AI Overview / Perplexity / ChatGPT visibility tracking
- **Athena AI** — competitor mention tracking in LLM responses
- **Otterly.AI** — AI search visibility analytics

**When to switch:** at ≥10 articles per year and ≥$10K marketing budget on content.

---

## Audit report template

```markdown
# LLM Visibility Audit — [Date]

> **Author:** [Auditor]
> **Articles audited:** [list]
> **Method:** [manual / semi-auto / professional]
> **Limitation:** [what couldn't be tested]

## TL;DR — 3–5 key findings

1. [Top finding with metric]
2. [Top finding with metric]
3. [Top finding with metric]

## Per-article analysis

### Article 1: "[Title]"

**Age:** [days since publish]

**Direct URL discoverability:** [yes/partial/no + details]
**Content citation in AI summaries:** [yes/partial/no + verbatim quotes found]
**Topic-specific queries verdict:** [results]

**Verdict:** [score X/10] — [1-line summary]

### Article 2: ...

## Cross-article insights

### What's working
- [pattern]
- [pattern]

### Where we lose
- [pattern]
- [pattern]

### Main insight
- [the takeaway that should change next month's content strategy]

## Recommendations (action plan)

### Quick wins (1–2 weeks)
1. ...
2. ...

### Baseline monitoring (2–4 weeks)
3. ...

### Strategic (quarter+)
4. ...

## Open questions to team

1. ...
2. ...

## Sources actually checked

- [URL 1]
- [URL 2]
```

---

## Decision rules — what to do with results

| Result pattern | Action |
|----------------|--------|
| Articles cited in Categories A + B + C, but not in D and E | Normal for LinkedIn-only. To win D/E — you need your own blog with SEO. **Don't panic.** |
| Articles NOT cited in any category after 4+ weeks | Indexation lag or broken structure. Check direct URL discovery. If URL is not found — refresh the article (new H2s, new concept, better lead paragraph). |
| Competitors cited on your topic queries | Check — are they calling your concept by their own name? If yes — that's plagiarism, respond via PR / DMCA. If not — your topic isn't sufficiently "yours", you need a more unique angle. |
| Citations growing over time | Continue — the pattern works. Don't change the structure. |
| Citations plateaued at 1–2 mentions | Likely the dominant LLM engine is caching one phrase. Try refreshing the article (new dates, new numbers) for a refresh. |

---

## Main insight from real audits

LinkedIn Articles are an **excellent "warm-up" for a warmed-up audience**, but **NOT a replacement for SEO** for cold top-of-funnel.

- Warmed-up audience (heard of you from somewhere): LLMs cite your articles in answers. ✅
- Unique concepts with their own names: LLMs cite them, even from a cold user. ✅
- Cold cold queries "Best [category] [year]": LinkedIn won't beat a company with a blog machine. ❌

**Strategy:** Articles for retention + warm discovery. SEO blog on your own domain for cold acquisition.

---

## Anti-patterns in auditing

| Anti-pattern | Why it's bad |
|--------------|--------------|
| Auditing 1 week after publication | Indexation lag (2–4 weeks). Nothing should be working yet. |
| Only Category A | Creates an illusion of visibility. Branded queries always work. |
| Only Google AI Overview | That's just 1 of 5 engines. ChatGPT and Perplexity have different retrieval signals. |
| One person runs it, nobody reviews | Confirmation bias. Minimum 2-person review. |
| Audit without recording competitor mentions | Without that there's no understanding of share-of-voice. |
| Action items without an owner and deadline | The audit becomes a shelf document. |

---

## Connection with the rest of the system

| Document | Role |
|----------|------|
| `LinkedIn-Articles-GEO-Framework.md` | How to create an article that will pass this audit |
| `Templates/Articles-Plan-Template.md` | Where to define "GEO target queries" in advance |
| `.claude/skills/audit-llm-visibility/SKILL.md` | A skill that automates part of the audit |
| `Growth-Loop-Architecture.md` | LLM citation rate can be added as a metric in the Growth Loop |
