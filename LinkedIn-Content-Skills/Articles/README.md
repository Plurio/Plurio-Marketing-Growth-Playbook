# Articles — Worked Examples + Plan Template

> 5 published LinkedIn Articles from the Plurio team as worked examples of the GEO methodology + a series plan template.

---

## What's inside

### `Articles-Plan-Template.md`

Plan template for an Articles series optimized for AI-search + the LinkedIn algorithm. Copy it and fill it in for your niche. Paired documents:

- `../Knowledge-Base/10-Articles-and-GEO/LinkedIn-Articles-GEO-Framework.md` — methodology
- `../Knowledge-Base/10-Articles-and-GEO/LLM-Visibility-Audit-Methodology.md` — how to verify it's working

### `_Examples/` — 5 worked examples

All 5 articles were published on LinkedIn Pulse by the author (Seva Ustinov, founder/CEO of Plurio). These are **not theoretical examples** — they're real production content that went through our system: `/create-article` → GEO checklist → publication → LLM visibility audit.

| File | Topic | What it demonstrates |
|------|-------|----------------------|
| `2026-04-07-how-ai-agents-manage-ad-budgets.md` | AI agents + ad budget management framework | Title=query, named concept ("trust adoption curve"), 5-level framework |
| `2026-04-16-five-stages-ai-agent-adoption.md` | 5 stages of AI-agent adoption in marketing teams | Numbered framework, persona-based progression |
| `2026-04-22-epidemiology-of-vibe-coding.md` | "Epidemiology" of vibe-coding as a cultural phenomenon | Cross-domain metaphor as named concept |
| `2026-04-29-why-your-crm-is-missing-30-40-of-lead-sources.md` | CRM attribution gap + open-source solution | Specific numeric anchor (30–40%) + product link (intake.plurio.ai) |
| `2026-05-05-how-performance-marketing-teams-use-ai-agents-3-cases.md` | 3 cases of AI-agent use in perf marketing | Case-driven structure, concrete numbers per case |

### What you can take from the examples

After reading the 5 articles, notice:

1. **Lead paragraph (first paragraph)** — a direct answer to the question in the title. No "let me set the context."
2. **H2 structure** — each section is self-contained, an LLM can extract it on its own.
3. **One named concept per article** — "trust adoption curve", "5 levels", "30–40% gap", "epidemiology of vibe-coding".
4. **Concrete numbers with context** — not "AI saves time", but "90 minutes → 10 minutes".
5. **Closing without a marketing CTA** — we've seen CTAs lower LLM trust.

### What you should NOT do

- ❌ Copy the article contents into your own content (this is our voice and our data).
- ❌ Use our named concepts as your own (create your own).
- ✅ **OK** to copy structure: title format, lead paragraph approach, H2 patterns, citation style.

---

## How to use it in your workflow

### If you have Claude Code

```bash
/create-article [Author] [topic]
```

The skill will read the examples + GEO Framework + author's DIP and generate a draft following the 8-step pipeline.

### Without Claude Code

1. Open `Articles-Plan-Template.md` — plan a series of 3 articles.
2. Read the 5 example articles in `_Examples/` — see the pattern in practice.
3. Open `../Knowledge-Base/10-Articles-and-GEO/LinkedIn-Articles-GEO-Framework.md` — the core methodology.
4. Write the article following the GEO checklist in the plan.
5. After 4 weeks — run the `audit-llm-visibility` skill or a manual audit using `LLM-Visibility-Audit-Methodology.md`.

---

## About Plurio (context that shows up in the articles)

Plurio is an AI agent for performance marketing teams at consumer software / fintech / edtech / healthtech companies. The agent manages $500M+/year in client media budgets. The articles describe real production experience running the agent for our clients.

More at [plurio.ai](https://plurio.ai). Open-source UTM tracking library: [intake.plurio.ai](https://intake.plurio.ai).
