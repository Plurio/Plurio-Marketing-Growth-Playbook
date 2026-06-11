# DIP Update Workflow — How to Update a Digital Identity Profile

> Instructions for incrementally updating an existing DIP.
> **CRITICAL PRINCIPLE:** A DIP is built ONLY from source materials — transcripts, meeting recordings, talks, podcasts. NEVER from posts. Posts are the OUTPUT of the DIP, not the INPUT. Building a DIP from posts that were written from a DIP creates a feedback loop that destroys the person's real voice within 3-4 cycles.

---

## DIP Data Sources (Hierarchy)

### SOURCES (Input) — Where We Get Identity From

This is what the person says in their own words, in real time. Spoken speech is the most honest source of identity.

| Priority | Source Type | Location | What We Extract |
|----------|-------------|----------|-----------------|
| 1 | **Podcasts and talks** (public) | `your-raw-sources/podcasts-and-events/` | Tone of voice, positions, stories, frameworks — verbatim |
| 2 | **Conferences** (public) | `Media activities/Cursor Case Activities/Conferences/` | Same + how they explain complex things simply |
| 3 | **Livestreams** (public) | `Media activities/Cursor Case Activities/Livestreams/` | Informal tone, spontaneous reactions |
| 4 | **AGI/Product weekly calls** (internal) | `your-transcripts/internal-product-calls/` | Current product positions, new insights, reactions to data |
| 5 | **Presales / Discovery calls** | `Presales/Projects/Projects list/*/Transcripts/` | How they pitch, how they explain value, client reactions |
| 6 | **Marketing strategy calls** | `your-transcripts/marketing-meetings/` | Strategic decisions, position shifts, new ideas |
| 7 | **AI positioning calls** | `your-transcripts/strategy-calls/` | Evolution of positioning, new frameworks |
| 8 | **Client production calls** | `Production/Projects/Projects list/*/Meetings transcripts/` | Real results, how they discuss with clients |
| 9 | **Granola weekly syncs** | `your-transcripts/synced-meetings/` | Operational context, current priorities |
| 10 | **Webinar transcripts** | `your-transcripts/webinars/` | Expert tone in public explanation |
| 11 | **Telegram posts** (their own words) | `your-raw-sources/telegram-posts/` | Informal voice, spontaneous thoughts |

### NOT SOURCES (Output) — Don't Look Here for Identity

| Type | Why Not |
|------|---------|
| **LinkedIn posts** (`Posted/`) | OUTPUT of the system. Building a DIP from posts = feedback loop → loss of identity |
| **PR commentary** (`Commentary-opportunities/`) | OUTPUT — repackaged content |
| **Presentations and slides** | Edited, polished content — not the live voice |
| **Product blurbs and marketing copy** | Marketing text, not the person's voice |
| **Third-party articles and research** | Not this person's words |

**The only exception:** Posts can be scanned ONLY for the Performance Log (which topics resonate with the audience) — but this is audience data, NOT speaker identity data.

---

## When to Update

| Trigger | Frequency | What to Do |
|---------|-----------|-----------|
| **Before creating content** | Every time | Fresh Scan (see below) |
| New transcript featuring the person | As they appear | Full transcript analysis |
| The author gave feedback ("I don't talk like that") | Immediately | Correct Tone of Voice + Feedback Log |
| Quarterly review | Every 3 months | Full check of all sections |

---

## Fresh Scan — Mandatory Pre-Step Before Content

**When:** BEFORE every `/create-post`, `/create-pr-commentary`, `/create-comment`, or any other content creation on behalf of the author.

**What to do:**

1. Open the author's DIP → check `Last Updated` and `Last transcript analyzed`
2. Find ALL new transcripts featuring the author that appeared after the last update
3. Quickly scan each new transcript (5 min per file):
   - New positions / changes to old ones?
   - New stories / examples with numbers?
   - New phrases / speech patterns?
   - New client cases (anonymize)?
4. If something substantial is found → update the DIP before creating content
5. If nothing new → mark the scan date, continue

**How to find new transcripts:**

```
# For Seva — search by name in recent files
grep -rl "Seva" your-transcripts/ your-raw-sources/ --include="*.md" | head -20
# Or by modification date
find your-transcripts/ -name "*.md" -newer [last-DIP-update-date]
```

**For the exact locations to search per author — see the Source Map in CLAUDE.md.**

---

## Workflow: New Transcript (20 min)

### Step 1: Read the Transcript

Focus ONLY on this person's speech. Skip the contributions of other participants.

### Step 2: Check Each DIP Section

| Section | Question | Action if "Yes" |
|---------|----------|-----------------|
| Tone of Voice | Are there NEW speech patterns not captured in the DIP? | Add to Speech Patterns with a verbatim quote |
| Expertise Clusters | Did NEW subtopics or opinions appear? | Add to the appropriate cluster |
| Expertise Clusters | Have the % weights of clusters changed? | Recompute the distribution |
| Frameworks | Are NEW frameworks or principles mentioned? | Add to section 4 |
| Stories Bank | Are there NEW stories, anecdotes, cases? | Add with category and source |
| Viral Angles | Were NEW angles or phrasings discovered? | Add to section 7 |
| Contrarian Positions | Have positions changed? Are there new ones? | Update/add |
| Metrics & Numbers | New numbers, results, data points? | Add to Stories Bank or Expertise Clusters |

### Step 3: Check for Contradictions

**Critical:** If a new transcript contradicts something in the DIP (the person changed their mind, shifted their approach), then:

1. Mark the old statement as `[DEPRECATED YYYY-MM-DD]`
2. Add the new version with a quote from the new transcript
3. Record this in the Update Log

Example:
```
**[DEPRECATED 2026-02-15]** ~~"AI agents aren't ready for production yet"~~
**[UPDATED]** "We launched agents in production with 3 clients" — Client Sync, 2026-02-15
```

### Step 4: Update the Source Index

Add the new transcript to the Source Index table:
- Date
- File path
- Type (Call / Podcast / Meeting / etc.)
- What was extracted

### Step 5: Update the Update Log

Record:
- Update date
- What changed
- Source (transcript)
- New version

---

## Workflow: Audience Performance Review (Separate from DIP)

Once 5+ posts have been published — we analyze, BUT this is audience data, not identity data.

**What we update:**
- `Performance Log` in the DIP → which topics/formats/hooks resonate
- `Format Preferences` → affinity based on data

**What we DON'T update based on posts:**
- Tone of Voice (only from transcripts)
- Expertise Clusters (only from transcripts)
- Stories Bank (only from transcripts)
- Speech Patterns (only from transcripts)
- Contrarian Positions (only from transcripts)

---

## Workflow: Quarterly Review (30 min)

Every 3 months — a full DIP review:

### Checklist

- [ ] **Unanalyzed transcripts:** Are there transcripts featuring the author that haven't been processed? (This is the top priority)
- [ ] **Tone of Voice:** Does it still accurately describe their speech? Compare with 2-3 recent transcripts
- [ ] **Expertise Clusters:** Does the % distribution match reality? Has the focus shifted?
- [ ] **Stories Bank:** Which stories have already been used (mark Once)? Are any outdated? Are there NEW ones from recent transcripts?
- [ ] **Editorial Rules:** Are the pillars still relevant?
- [ ] **Differentiation:** Have authors started overlapping on topics?
- [ ] **Contrarian Positions:** Are any outdated? Have any become mainstream?
- [ ] **Metrics & Numbers:** Are the numbers current? (team size, clients, results all change)

---

## Ways to Update the DIP

### 1. Through the Agent (recommended)

Tell the agent what needs to change — it will update the DIP with versioning and an Update Log entry.

**Examples:**
- "Update Seva's DIP from this transcript" → the agent will analyze and update all relevant sections
- "Remember: I don't say leverage" → the agent adds it to "They NEVER say" + Feedback Log
- "Update the DIP: add the story about..." → the agent adds it to Stories Bank + Update Log

**What the agent does automatically:**
- Checks for contradictions with the existing DIP
- Increments the version (1.0 → 1.1)
- Writes an entry in the Update Log
- Notes the source of every change (ALWAYS a transcript, NEVER a post)

### 2. Direct Editing (allowed)

You can open the DIP file and edit it manually. Three rules:

1. **Don't delete sections.** If something is outdated — mark it `[DEPRECATED YYYY-MM-DD]`
2. **Add an entry to the Update Log** at the bottom of the file: date + what changed + source (transcript)
3. **Increment the version** in the header: minor update = +0.1, major restructure = +1.0

---

## Update Rules

1. **Source of truth = transcripts.** Only what the person said in their own words in a recorded conversation
2. **Posts ≠ source.** Posts are OUTPUT of the system, not INPUT. Using posts for the DIP = feedback loop
3. **Never delete** — mark as [DEPRECATED] with a date
4. **Always cite the source** — specific transcript, date, timestamp if available
5. **Increment version** — 1.0 → 1.1 on a minor update, → 2.0 on a major restructure
6. **Update Log is mandatory** — every change is logged
7. **Fresh Scan is mandatory** — before any content creation, check recent transcripts
