# LinkedIn Post Benchmark Validation System

**Purpose:** Ensure every LinkedIn post is grounded in data, validates against market benchmarks, and tracks sources properly.

**Created:** 2026-02-13
**Last updated:** 2026-02-13

---

## Overview

When creating a LinkedIn post, validate claims against three layers:

1. **Internal Circle** — Our transcripts, client meetings, product data
2. **External Circle (Benchmarks)** — Industry reports with hard numbers
3. **Trend Layer** — Competitor content, market signals

---

## 1. Benchmark Validation Table

Every post draft should include this table:

```markdown
## Benchmark Validation

| Claim in post | Supporting benchmark | Source | Report date | Freshness | Status |
|---------------|---------------------|--------|-------------|-----------|--------|
| [Your claim] | [Verbatim quote] | [Report name] | [Q/Year] | [Fresh/OK/Stale] | [Confirms/Supports/Contradicts/New] |
```

### Status definitions
- **Confirms** — External data directly proves the claim
- **Supports** — External data aligns with the claim direction
- **Contradicts** — External data challenges the claim (requires adjustment or acknowledgment)
- **New** — Claim is our original thesis, no external data yet (mark as opinion/prediction)

### Freshness rules
- **Fresh** (2026 data) — High confidence, cite freely
- **OK** (2025 H2 data) — Valid, add context if needed
- **Stale** (2025 H1 or older) — Mark as "historical context" or update

---

## 2. Source Reference Format

### In-post citation (when using stats)
> "According to [Report Name] ([Year], [Sample Size]), [stat]."

Example:
> "According to Jasper's State of AI in Marketing 2026 (1,400 marketers), 91% of marketing teams now use AI."

### Source tracking (in draft metadata)
```markdown
## Sources Used
- Jasper State of AI 2026 (Q1 2026) — AI adoption, governance, ROI
- External Web2App benchmark report (Q1 2026) — Web2App benchmarks
- Adapty State of Subscriptions 2025 (Q4 2025) — Subscription metrics
```

---

## 3. Available Benchmark Sources

### Tier 1: Fresh & Highly Relevant (2026)

| Source | Topics | Location |
|--------|--------|----------|
| **Jasper State of AI 2026** | AI adoption, governance, ROI, team structure | `your-benchmark-library/` |
| **External Web2App benchmark report** | Web2App funnels, conversion, LTV, payments | external benchmark reports |

### Tier 2: Recent & Relevant (2025 H2)

| Source | Topics | Location |
|--------|--------|----------|
| **Adapty State of In-App Subscriptions 2025** | Paywalls, pricing, retention, A/B testing | `your-benchmark-library/` |
| **Smartly Digital Advertising Trends 2026** | Ad automation, creative optimization | `your-benchmark-library/` |
| **AdQuantum Q5 Guide** | Seasonal spend, CPM dynamics | `your-benchmark-library/` |

### Full Index
See: `your-benchmark-library/`

---

## 4. Quick Validation Checklist

Before publishing a post, verify:

- [ ] **Claims have sources** — Every stat or strong claim traced to a benchmark
- [ ] **Dates are noted** — Report date recorded for each source
- [ ] **Freshness checked** — Stale data flagged or contextualized
- [ ] **No contradictions** — If external data contradicts, either adjust claim or explicitly acknowledge the difference
- [ ] **Internal + External aligned** — Our experience matches (or interestingly differs from) market data

---

## 5. Example: Validated Post Draft

### Post topic: "AI governance is the new bottleneck"

#### Draft text
> Everyone talks about AI adoption. But the real story in 2026?
>
> Governance is now the #1 blocker to scaling AI in marketing.
>
> According to Jasper's latest report (1,400 marketers surveyed), legal, compliance, and brand review processes jumped to the top constraint — a 3.4x increase from 2025.
>
> Meanwhile, 91% of teams use AI, but only 12% can execute multi-asset campaigns in days or hours.
>
> The gap isn't tools. It's workflows with governance built in.
>
> That's exactly what we're building at Plurio.

#### Benchmark Validation

| Claim | Supporting benchmark | Source | Date | Status |
|-------|---------------------|--------|------|--------|
| "Governance is #1 blocker" | "Legal, compliance & brand review processes are now the leading constraint on AI scale." | Jasper State of AI 2026 | Q1 2026 | Confirms |
| "3.4x increase from 2025" | "more than tripled from 2025" | Jasper State of AI 2026 | Q1 2026 | Confirms |
| "91% of teams use AI" | "91% of marketing teams use AI" | Jasper State of AI 2026 | Q1 2026 | Confirms |
| "Only 12% can execute fast" | "Just 12% are able to execute in days or hours" | Jasper State of AI 2026 | Q1 2026 | Confirms |
| "Gap isn't tools, it's workflows" | "True speed only emerges when AI is embedded into coordinated workflows" | Jasper State of AI 2026 | Q1 2026 | Supports |

#### Sources Used
- Jasper State of AI in Marketing 2026 (Q1 2026) — external Jasper report

---

## 6. Workflow Integration

### When creating a post:

1. **Draft the post** — Write your core message
2. **Identify claims** — List statements that need validation
3. **Check benchmarks** — Search `your-benchmark-library/` for supporting data
4. **Fill validation table** — Document sources and dates
5. **Adjust if needed** — Soften claims without support, strengthen claims with data
6. **Add citations** — Include attribution in post where impactful
7. **Save with metadata** — Store draft with validation table attached

### File naming for drafts
```
Posted/LinkedIn/Seva/YYYY-MM-DD-post-slug.md
```

Each file should contain:
- Post text
- Benchmark Validation table
- Sources Used section

---

## 7. Future: Competitor Content Tracking

Coming next:
- [ ] Competitor LinkedIn monitoring (what topics work)
- [ ] Virality pattern analysis
- [ ] Topic trend detection

Location: `your-benchmark-library/` (to be created)

---

## Related Documents

- [Benchmarks—Overview.md](../Content%20Machine%20Building/Benchmarks—Overview.md) — Master index of all benchmarks
- [Benchmarks—Metrics-Library.md](../Content%20Machine%20Building/Benchmarks—Metrics-Library.md) — Verbatim metrics by topic
- [LinkedIn Content Strategy Seva.md](LinkedIn%20Content%20Strategy%20Seva.md) — 4 editorial pillars
- [LinkedIn Viral Post Guidelines.md](LinkedIn%20Viral%20Post%20Guidelines.md) — Post structure best practices
