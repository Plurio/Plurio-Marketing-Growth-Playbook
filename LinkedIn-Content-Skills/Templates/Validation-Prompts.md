# Validation Prompts — Manual Validation Without Skills

> These prompts can be used in any AI tool (ChatGPT, Claude, etc.)
> to check content using the same methodology as the automated skills.

---

## How to Use

1. Copy the prompt you need
2. Paste your content in place of `[INSERT CONTENT]`
3. Run it in your AI tool
4. Fix the issues it finds
5. Re-run the check after edits

**Recommended order:** Facts → Generic → Sources → AI detection → Generic #2

---

## 1. Check Facts

```
Check the factual accuracy of this content. For each claim:

1. Mark it as FACT, OPINION, or INTERPRETATION
2. If it's a fact — verify:
   - Are the numbers accurate? (dates, percentages, amounts)
   - Are there contradictions inside the text?
   - Is any data outdated?
3. If drawn from multiple sources — is there a "compilation" issue (mixing facts from different contexts)?

Response format:
- OK: [claim]
- Check: [claim] — [why it's questionable]
- Error: [claim] — [what's wrong]

CONTENT:
[INSERT CONTENT]
```

---

## 2. Check Generic (generic language check)

```
Check this content for generic / AI language. Look for:

1. **AI phrases:** "in today's landscape", "leverage", "game-changer", "ecosystem",
   "delve into", "it's worth noting", "at the end of the day"
2. **Empty statements:** phrases that sound smart but carry no specifics
   ("AI is transforming the industry", "data-driven decisions")
3. **Buzzwords without definition:** terms that are used but never explained
4. **Repeated structure:** identical sentence constructions back-to-back
5. **Excessive positivity:** everything is "amazing", "incredible", "powerful"

For each issue:
- Quote from the text
- Why it's a problem
- A specific replacement (in the author's voice)

CONTENT:
[INSERT CONTENT]

AUTHOR'S STYLE (brief):
[Describe: direct/casual/formal, with numbers/without, humorous/serious]
```

---

## 3. Check Sources

```
Build a source map for this content. For EACH claim, determine:

| Claim | Type | Source |
|-------|------|--------|
| [quote] | Direct Quote / Inference / Data / General Knowledge / Unverifiable | [where from] |

Separately flag:
- Claims with no source (potentially invented)
- Claims where the source is unclear
- Numbers not tied to a specific context

CONTENT:
[INSERT CONTENT]

SOURCES (if any — transcript or material the content was written from):
[INSERT SOURCE]
```

---

## 4. Detect AI

```
Analyze this content on 6 levels of AI detection:

### Level 1: Vocabulary
- Any typical AI words? (leverage, ecosystem, delve, landscape, harness, pivotal)
- Any "signature" AI constructions? (It's worth noting, One thing that stands out)

### Level 2: Sentence Structure
- All sentences the same length? (AI writes ~15-20 words flat)
- Is there variation: short clipped phrases, long ones, cut-offs?

### Level 3: Formatting
- Excessive structuring? (lists where a human wouldn't use them)
- Transitions between paragraphs too neat?

### Level 4: Tone
- Tone flat throughout the text? (Humans swing: serious → joke → frustration → hope)
- Are there emotional "peaks"?

### Level 5: Content
- General statements without specifics?
- Everything "on the safe side"? (AI avoids controversial positions)
- Are there real insights, ones you wouldn't find in the top-10 Google results?

### Level 6: Rhythm (prose rhythm)
- Predictable rhythm? (long — long — long)
- Any unexpected "breaks"? (Humans cut off a thought. AI doesn't.)

Format: for each level — a score (1-5), issues found, specific edits.

CONTENT:
[INSERT CONTENT]
```

---

## 5. Quick Checklist (quick pre-publish check)

```
Check this post against the checklist:

HOOK:
- [ ] Do the first 140 characters stop the scroll?
- [ ] No generic opener ("In today's world...")?

CONTENT:
- [ ] Are there concrete examples / numbers?
- [ ] First person (I/my, not we/our)?
- [ ] One main idea (not 5 topics in one post)?

STRUCTURE:
- [ ] Paragraphs 1-3 lines?
- [ ] Whitespace present (not a wall of text)?
- [ ] No links in the first 300 characters?

CTA:
- [ ] A specific question / call to action?
- [ ] Not engagement bait ("Agree?")?

AI CHECK:
- [ ] No AI phrases (leverage, ecosystem, landscape)?
- [ ] Emotional swings present?
- [ ] Sounds like a real person, not a press release?

CONTENT:
[INSERT CONTENT]
```

---

## Bonus: Universal Validation Prompt (all-in-one)

> Use this if you need a quick check without running 5 separate prompts.

```
Check this content against 5 criteria. Be strict — better to over-flag than miss an issue.

1. FACTS: numbers accurate? no contradictions? no outdated data?
2. GENERIC: any AI phrases? empty statements? buzzwords?
3. SOURCES: is every claim sourced from somewhere, or invented?
4. AI PATTERNS: same-length sentences? flat tone? no "breaks"?
5. CHECKLIST: hook < 140 chars? first person? specific CTA? no links up front?

For each issue: quote → why it's a problem → a specific edit.

At the end: overall score 1-10 and TOP-3 most critical edits.

CONTENT:
[INSERT CONTENT]

AUTHOR (style): [briefly describe the author's style]
PLATFORM: [LinkedIn / X / Telegram / ...]
```
