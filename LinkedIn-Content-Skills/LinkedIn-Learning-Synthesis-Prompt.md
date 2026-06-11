# LinkedIn Learning → Growth Plan & Loop — Synthesis Prompt

> **What this is:** a meta-instruction (prompt) for an AI agent or a person who needs to convert a library of external LinkedIn courses (LinkedIn Learning, YouTube courses, books, podcasts) into a practical Growth Plan and Growth Loop, without copying copyrighted material.
>
> **Why not just copy the courses themselves:** LinkedIn Learning transcripts are protected by copyright. The useful output is not quotes, but a **structured distill**: what frameworks/patterns/rules/anti-patterns the sources contain, and how they map into your system.

---

## 1. When to use this prompt

- You bought a LinkedIn Learning subscription (or a similar source) and want to systematize the knowledge instead of vaguely "I'll watch it someday."
- You're preparing your Growth Plan and want to verify you haven't missed a category of levers.
- Onboarding a new content creator — you hand them the source library and want a distillate within a day, not a month.
- You want to update your current Algorithm Intelligence / Hook Library / DIP template with new data from authoritative sources.

---

## 2. Categories of LinkedIn courses that most often cover growth

Any good LinkedIn course library splits into 6 functional blocks. Use this list as a checklist for "what must be represented in my source-material library":

| Block | What it covers | Typical course names |
|------|---------------|-------------------------|
| **Profile foundations** | Headline, About, Experience, Skills, Photo, Banner, Verifications | "Rock your LinkedIn profile", "Optimizing your LinkedIn profile" |
| **Personal branding** | Voice, niche, positioning, who you serve, story arc | "Personal branding strategies", "Build a strong professional brand" |
| **Algorithm understanding** | How the feed ranks, signals, distribution, penalties | "Marketing on LinkedIn", internal LinkedIn research articles |
| **Content creation craft** | Hooks, structure, formats, frameworks, storytelling | "Create LinkedIn posts that stand out", "Storytelling and content creation", "Strategies for creating viral short-form content" |
| **Engagement strategy** | Comments, DMs, networking, building relationships | "CMO's guide to engaging on LinkedIn", "Executive's guide to engaging on LinkedIn", "How to stand out on LinkedIn" |
| **Business/page strategy** | Company pages, B2B, lead gen, social selling | "B2B marketing on LinkedIn", "Growing your business with LinkedIn Pages", "Content strategy in the age of AI" |

If your library covers <4 of the 6 blocks — there's a gap; add material before the distill.

---

## 3. Prompt for the LLM (or for a research-savvy colleague)

> **Copy the text below and feed it to the agent together with the link/path to your source library.**

```
TASK: Distill the attached library of LinkedIn-growth courses/transcripts/articles into 
two artifacts that I can drop into my Growth Plan and Growth Loop without copying any 
copyrighted text.

OUTPUT 1 — "Growth Plan additions" — extracted patterns, structured as:

  For each FUNCTIONAL BLOCK (Profile / Branding / Algorithm / Content / Engagement / Pages):
    - 3–7 concrete rules or frameworks the sources agree on
       (each rule = one sentence; cite the SOURCE NAME, not a quote)
    - 1–3 contrarian or debated points where sources disagree
       (note both positions; flag which is more recent or authoritative)
    - 1–3 anti-patterns ("never do X, because Y")
    - Quantitative benchmarks IF sources provide any
       (numbers only; never copy phrasing — express as: "Sources A and B cite ~X% baseline ER")

OUTPUT 2 — "Growth Loop additions" — operational changes to make, structured as:

  For each STAGE of the loop (Targets / Create / Collect / Analyze / Adjust):
    - What sources suggest tracking that I might not be tracking yet
    - What review cadence sources recommend (daily / weekly / monthly checks)
    - What specific signals indicate "the loop is working" vs "broken"
    - What tools sources mention (named tool list, no endorsements)

CONSTRAINTS:
- DO NOT copy verbatim sentences from sources. Paraphrase in your own words.
- DO NOT include speaker names in a way that puts words in their mouth.
  Format: "Source 'Course Name' argues that X." (not "Speaker N said quote")
- DO NOT invent numbers. If sources don't give a number, write "(no benchmark in sources)".
- Mark each item with the source name in [brackets] so I can trace it back.
- If 2+ sources contradict, surface the disagreement — don't pick a winner silently.
- Output ONLY the two artifacts. No preamble, no recap of what you read.

Length budget: ~1500 words OUTPUT 1, ~800 words OUTPUT 2.
```

---

## 4. What to do with the result

### Step 1 — merge into existing documents

Distribute the resulting OUTPUT 1 across the existing files:

| Distillate category | Where to add |
|----------------------|---------------|
| Profile foundations | `Knowledge-Base/08-Profile-Optimization/Profile-Optimization-Guide.md` |
| Personal branding rules | `Templates/DIP-Template.md` (sections "Voice", "Positioning") |
| Algorithm patterns | `Knowledge-Base/02-LinkedIn-Algorithm/Algorithm-Intelligence.md` |
| Hook frameworks | `Knowledge-Base/03-Viral-Trends/Hook-Pattern-Library.md` |
| Anti-patterns | `Knowledge-Base/03-Viral-Trends/Anti-Patterns.md` |
| Content formats | `Knowledge-Base/05-Format-Testing/Format-Catalog.md` |
| Engagement / commenting | `Knowledge-Base/06-Comments-Engine/Comments-Engine.md` |
| Cadence / posting times | `Knowledge-Base/02-LinkedIn-Algorithm/Posting-Time-Guidelines.md` |
| Business / pages strategy | New file (not in default scope; add it if you run a company page) |

### Step 2 — OUTPUT 2 → Growth Loop update

Take the resulting OUTPUT 2 and walk through `Growth-Loop-Architecture.md` sections:
- **TARGETS:** add new metrics if the sources propose them.
- **COLLECT:** add new signals to collect.
- **ANALYZE:** add new review questions to the monthly review.
- **ADJUST:** add new triggers for target recalculation.

### Step 3 — recalibration

After adding the distillate — revisit your current Growth Plan. If the distillate points to gaps (e.g., "you don't track dwell time, but it's a Top-3 signal in X sources") — add to the Spreadsheet and start collecting.

---

## 5. What you should NOT output

- **Full course transcripts** — copyright violation.
- **Verbatim quotes longer than 1 sentence** — fair-use territory; better to paraphrase.
- **Authoritative "rules" without source attribution** — if the LinkedIn algorithm changes tomorrow, you need to know where the rule came from so you can re-evaluate.
- **Marketing slogans from the courses** ("master LinkedIn in 30 days") — discard them, capture only the operational substance.

---

## 6. Distillate quality check

After receiving OUTPUT 1 + OUTPUT 2 — run through the checklist:

- [ ] Does every item have a source noted in [brackets]?
- [ ] Are there no verbatim sentences longer than 8–10 words from the source?
- [ ] Numbers (if any) — is the source they came from indicated? If not, is it marked "(no benchmark)"?
- [ ] Are contradictions between sources NOT collapsed into a single "right answer"?
- [ ] Is every item actionable (can be turned into a row in the Growth Plan or Growth Loop)?
- [ ] No generic phrases like "create valuable content" — only concrete specifics?

If the checklist fails on ≥3 items — re-run the distill with a refined prompt.

---

## 7. Alternative — manual distill in 1 day

If LLM-distill isn't suitable (NDA, trust, accuracy), here's the manual mode:

1. **Source list** (15 minutes): list every course/book/podcast in the library.
2. **6 sheets** (one per functional block from section 2): go through sources → write 1 line into the appropriate sheet.
3. **Pass through sources** (4–6 hours for 15–20 sources at 2x speed): pause on new concepts, write into the sheets.
4. **Dedupe + merge** (1 hour): merge duplicate items, keep the cite to the most authoritative source.
5. **Drop into system files** (1 hour): distribute according to the table in step 4.1.

Total: 1 working day. Result is comparable to LLM-distill but 100% accurate in terms of trust.

---

## 8. When to refresh the distillate

- **Every 6 months:** if you work in the LinkedIn niche, the algorithm changes. Sources older than 12 months risk being outdated. Re-run distill on new courses.
- **When you see a systemic deviation** in metrics (ER falling for 3 months, or Saves Rate not growing despite actions): there may be an insight in newer sources that isn't in your current system. Trigger for fresh research.
- **When content focus changes** (was personal brand → moving to a company page; or B2C → B2B): you need a distill in the new category.
