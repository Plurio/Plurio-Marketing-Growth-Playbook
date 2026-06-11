# Plurio Marketing Growth Playbook

> Public-facing playbooks, skills, and templates from the Plurio marketing team.
> Open-source operational artifacts — what we use internally to grow on LinkedIn, structure content systems, and build agent-driven workflows for performance marketing teams.

---

## What's inside

### [LinkedIn-Content-Skills/](LinkedIn-Content-Skills/)

A complete LinkedIn content system: framework for creating posts and long-form articles, profile optimization for the algorithm, hook library, Digital Identity Profile + Voice Vocabulary templates, and 19 ready-to-use Claude Code skills (`/create-post`, `/create-article`, `/optimize-profile`, `/validate-content`, `/audit-llm-visibility`, ...).

**Paired documents for systematic growth:**

- [LinkedIn-Content-Skills/Growth-Plan-Template.md](LinkedIn-Content-Skills/Growth-Plan-Template.md) — causal model + Google Sheets formulas + quarterly strategy.
- [LinkedIn-Content-Skills/Growth-Loop-Architecture.md](LinkedIn-Content-Skills/Growth-Loop-Architecture.md) — closed-loop architecture: targets → create → collect → analyze → adjust.
- [LinkedIn-Content-Skills/LinkedIn-Learning-Synthesis-Prompt.md](LinkedIn-Content-Skills/LinkedIn-Learning-Synthesis-Prompt.md) — meta-prompt for distilling external LinkedIn courses into your own Growth Plan/Loop without copying copyrighted material.

**Long-form Articles + AI-search optimization (GEO):**

- [LinkedIn-Content-Skills/Articles/](LinkedIn-Content-Skills/Articles/) — 5 worked examples of Articles actually published by the Plurio team + a series plan template.
- [LinkedIn-Content-Skills/Knowledge-Base/10-Articles-and-GEO/LinkedIn-Articles-GEO-Framework.md](LinkedIn-Content-Skills/Knowledge-Base/10-Articles-and-GEO/LinkedIn-Articles-GEO-Framework.md) — methodology for creating Articles optimized for ChatGPT/Perplexity/Google AI citations.
- [LinkedIn-Content-Skills/Knowledge-Base/10-Articles-and-GEO/LLM-Visibility-Audit-Methodology.md](LinkedIn-Content-Skills/Knowledge-Base/10-Articles-and-GEO/LLM-Visibility-Audit-Methodology.md) — how to check whether LLM engines actually cite your content.
- [LinkedIn-Content-Skills/Hook-Bank.md](LinkedIn-Content-Skills/Hook-Bank.md) — working hook library with persona × awareness mapping.

**Detailed overview:** [LinkedIn-Content-Skills/README.md](LinkedIn-Content-Skills/README.md)

---

## Who this is for

- **Founders** and **executives** who want to grow systematically on LinkedIn instead of "posting when inspiration strikes."
- **Marketing teams** building content engines with AI agents in the loop, not as a replacement for human expertise.
- **Solo creators** without a team but with Claude Code / Cursor.
- **Marketing ops** for consumer software, fintech, edtech, healthtech — long funnels, subscription models.

---

## How to use it

1. **Read** [LinkedIn-Content-Skills/README.md](LinkedIn-Content-Skills/README.md) — a 15-minute overview of the architecture.
2. **Build** your first DIP using [LinkedIn-Content-Skills/Templates/DIP-Template.md](LinkedIn-Content-Skills/Templates/DIP-Template.md) — 2–3 hours per author.
3. **Copy** `LinkedIn-Content-Skills/.claude/skills/` into your own repo if you use Claude Code, or use `Templates/Validation-Prompts.md` for manual work.
4. **Configure** your Growth Plan using [LinkedIn-Content-Skills/Growth-Plan-Template.md](LinkedIn-Content-Skills/Growth-Plan-Template.md) — collect three months of baselines, calibrate the formulas.
5. **Run** monthly reviews using [LinkedIn-Content-Skills/Growth-Loop-Architecture.md](LinkedIn-Content-Skills/Growth-Loop-Architecture.md).

---

## What's NOT included (intentionally)

- **Tone of voice for specific people** (Digital Identity Profiles of named authors + Voice Vocabularies) — these are personal artifacts and aren't published. Templates for building your own are included.
- **Sample published posts** of specific authors (short-form) — each team builds its own library from its own posts. Articles are public on LinkedIn Pulse, so 5 examples are included.
- **Specific Claude Code slash commands tied to our internal infrastructure** (PR comments for journalists, event skills, partnership ops) — that's a separate domain. This repo covers only the LinkedIn content + Articles + GEO layer.
- **LinkedIn Learning transcripts section** — copyright; instead, we provide a meta-prompt for building your own distillation ([LinkedIn-Learning-Synthesis-Prompt.md](LinkedIn-Content-Skills/LinkedIn-Learning-Synthesis-Prompt.md)).
- **LinkedIn GEO Guide PDF (external)** and **GEO Checklist PDF** — third-party copyright. Used as reference; the methodology has been synthesized into our open documents.

---

## License

MIT — see [LICENSE.md](LICENSE.md). Free to copy, adapt, and use in commercial projects. Attribution is appreciated but not required.

---

## Plurio

[Plurio](https://plurio.com) is an AI agent that **runs the daily performance marketing loop** for consumer software: subscription apps, AI services, fintech, edtech. It doesn't "assist" — it **acts**: adjusts bids, reallocates budgets, generates creatives, and monitors creative fatigue. It works alongside the team as another senior performance marketer.

The agent manages **$500M+/year** in client media budgets. Client results: 2x sales, CAC down 20%+.

Everything in this repo is the methodology we use ourselves to grow on LinkedIn. We open-sourced it because we believe AI-native performance marketing teams are what the future looks like, and building in public accelerates adoption across the industry.
