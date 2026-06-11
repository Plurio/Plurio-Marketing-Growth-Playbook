# DIP Creation Workflow — How to Build a Digital Identity Profile

> Step-by-step instructions for creating a complete DIP from scratch.
> Time: 3-5 hours per person (depending on transcript volume).

---

## Prerequisites

- At least 3-5 transcripts featuring the person (calls, podcasts, meetings, webinars)
- Access to the template: `_DIP-Template.md`

**CRITICAL PRINCIPLE:** A DIP is built ONLY from source materials — transcripts, meeting recordings, talks, podcasts. NEVER from posts. Posts are the OUTPUT of the DIP, not the INPUT. Building a DIP from posts creates a feedback loop and destroys the author's real voice within 3-4 cycles.

---

## Phase 1: Gather Sources (30 min)

### Where to Find Transcripts

Use the transcript map from CLAUDE.md:

| Type | Location |
|------|----------|
| Presales calls | `Sales/Presales/Projects/Projects list/*/Transcripts/` |
| Client meetings | `Production/Projects/Projects list/*/Meetings transcripts/` |
| AGI/Product calls | `your-transcripts/internal-product-calls/` |
| Granola (working) | `your-transcripts/synced-meetings/` |
| Marketing calls | `your-transcripts/marketing-meetings/` |
| Podcasts/events | `your-raw-sources/podcasts-and-events/` |
| Webinars | `your-transcripts/webinars/` |
| Conferences | `Media activities/Cursor Case Activities/Conferences/` |
| Livestreams | `Media activities/Cursor Case Activities/Livestreams/` |

### What to Collect

1. **Transcripts** — at least 3, ideally 5+. Diversity of types matters more than quantity: better to have 1 podcast + 1 client call + 1 internal meeting + 1 webinar than 5 identical calls.
2. **Telegram posts or voice notes** — if available, in the person's own words (not rewritten)
3. **Existing profiles** — check `Skills/` for any Tone-and-Expertise documents for this person

**DO NOT collect:** LinkedIn posts (`Posted/`), PR commentary, presentations, marketing copy — these are all OUTPUT, not the person's voice.

### Phase Output

A list of 5-10 source files with paths, ready for analysis.

---

## Phase 2: Extract Tone of Voice (60 min per transcript)

### What to Do

Read each transcript, focusing **ONLY on this person's speech** (skip other participants).

### What to Extract

**1. Style characteristics:**
- Formal or informal?
- Technical or accessible?
- Emotional or analytical?
- Type of humor (if any)?
- Sentence length: short and clipped, or long and expansive?

**2. Speech patterns (record VERBATIM):**
- Signature phrases that repeat across transcripts
- How they begin an explanation
- How they express disagreement
- How they express enthusiasm
- How they transition between topics
- How they close a thought

**3. Language rules:**
- Which words do they use often?
- Which words do they NEVER use?
- How do they address others?
- Any slang, jargon, or specific terminology?

### Quality Criterion

Every statement in the Tone of Voice section must be backed by a **verbatim quote** from a transcript, with source and date. No generalizations without evidence.

**Bad:** "Speaks directly and specifically"
**Good:** "Speaks directly and specifically: 'Don't make it pretty, make it work' — AGI Weekly, 2026-02-10"

---

## Phase 3: Build Expertise Clusters (30 min)

### What to Do

From all transcripts, compile a list of EVERY topic this person speaks about.

### How to Categorize

1. Group topics into 3 clusters (maximum 4)
2. Assign a % weight to each cluster based on frequency of mention
3. For each cluster:
   - 3-5 subtopics
   - The person's specific position/opinion on each subtopic
   - 2-3 verbatim quotes as evidence
   - Unique angle: how does THIS person talk about it DIFFERENTLY than everyone else

### How to Identify the Unique Angle

Ask yourself: "If 10 experts were speaking on this topic, what would THIS person say differently?"

**Example:**
- Topic: AI agents in marketing
- Generic expert: "AI agents automate routine work"
- Kirill: "I stopped opening dashboards 3 weeks ago — the agent does it for me. But we're still tuning it, I won't lie"

The difference: honesty ("I won't lie") + specific personal experience ("3 weeks ago").

---

## Phase 4: Build the Stories Bank (30 min)

### What to Do

From the transcripts, extract EVERY story, anecdote, case, and personal example. The source is only the person's recorded speech.

### Story Categories

**Professional:**
- Client stories — results with clients (with specific numbers)
- Product stories — why we built X, what didn't work with Y
- Team stories — how the team operates, decisions, conflicts
- Failure stories — what didn't work and what the lesson was

**Personal:**
- Life stories — moves, family, decisions
- Learning stories — what shifted their thinking
- Hobby/interest stories — what they do outside work

### For Each Story, Record

1. **Short title** — for quick lookup
2. **Specific detail** — the most memorable moment (a number, fact, quote)
3. **Reusable?** — Yes (can be used again) / Once (already used) / Anonymize (needs anonymization)
4. **Source** — where it was extracted from

---

## Phase 5: Set Editorial Rules (20 min)

### Content Pillars

Define 3-4 content pillars based on:
- Expertise Clusters (from Phase 3)
- Company positioning (from CLAUDE.md ICP)
- What this person WANTS to be known for (if they've said so)

Assign % distribution. Typical breakdowns:
- Primary pillar: 35-40%
- Second: 25-30%
- Third: 15-20%
- Fourth (if any): 10-15%

### Differentiation

Fill out the table: how this person differs from other authors on the team.

|--|-------------|------|--------|--------|------|
| Focus | ? | Vision | Execution | Architecture | Process |
| Tone | ? | Strategic | Practical | Direct | Storytelling |
| Audience | ? | CTOs/founders | CMOs/growth | Engineers/PM | Marketing |

---

## Phase 6: Identify Viral Angles (20 min)

### What to Do

Analyze transcripts for:
- Which phrasings get a reaction from the other participants? (listen for reactions from interviewers, colleagues)
- Which stories do people ask follow-ups about / comment on?
- Which topics cause debate or surprise?

### Identify 3-5 Signature Angles

For each:
- Angle name
- When to use it
- Why it works (psychology)
- Example hook in this person's voice

### Adapt Standard Hook Formulas

Take the formulas from `03-Viral-Trends/Hook-Pattern-Library.md` and rewrite each in this person's voice.

---

## Phase 7: Bootstrap Format Preferences and Performance Log (10 min)

1. Based on content type and the author's speaking style → recommend formats from `05-Format-Testing/Format-Catalog.md`
2. Create an empty Performance Log (populated after publication)
3. The Performance Log tracks audience response — this is audience data, NOT speaker identity data

---

## Phase 8: Validation (15 min)

### Test 1: Voice Test

Read the DIP from start to finish. Ask: **"Could someone who has NEVER met this author write a convincing post in their voice, using ONLY this document?"**

- If no → where is the specificity missing? Add verbatim quotes.

### Test 2: Specificity Test

Check every section: **"Is there a single statement without a concrete example or quote?"**

- If yes → either add a quote, or remove the statement.

### Test 3: Differentiation Test

Replace the author's name with the name of another team member. **"Does this DIP fit another person?"**

- If yes → the DIP is too generic. It needs more uniqueness.

---

## Output

A finished `{Name}-DIP.md` file in the `01-Digital-Identity-Profiles/` folder, populated according to the `_DIP-Template.md` template, with:
- At least 10 verbatim quotes
- 3 expertise clusters with % weights
- 5+ stories in the Stories Bank
- 3-5 viral angles with hook examples
- A completed differentiation table

Save the file and update the Source Index with the dates of all analyzed transcripts.
