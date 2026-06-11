# Weekly Update Workflow — Content Machine Auto-Refresh

> Weekly process for updating all Content Machine skill documents.
> Goal: always be up to date on algorithm changes, trends, and new author materials.
> **Last updated:** 2026-02-19

---

## Schedule

| Day | Task | Documents |
|------|--------|----------|
| **Monday** | Algorithm & Trends Refresh | Algorithm-Intelligence.md, Current-Trends.md, Anti-Patterns.md |
| **Wednesday** | Content Scan: new author materials | DIP Source Index (each author), Performance-Log.md |
| **Friday** | Post Performance Review + Next Week Planning | Performance-Log.md, Experiment-Backlog.md, content plans |

---

## TASK 1: Algorithm & Trends Refresh (Monday)

### 1.1 LinkedIn Algorithm Update

**What to check:**
1. New algorithm research (Richard van der Blom, Buffer, SocialInsider, Hootsuite)
2. Official LinkedIn announcements (LinkedIn Engineering Blog, LinkedIn News)
3. Changes in recommendations from practitioners (Jasmin Alic, Lara Acosta, Justin Welsh)

**Search queries:**
- "LinkedIn algorithm update 2026"
- "LinkedIn algorithm changes [current month]"
- "LinkedIn engagement rate benchmark 2026"
- "Richard van der Blom LinkedIn insights"

**What to update:**
- `02-LinkedIn-Algorithm/Algorithm-Intelligence.md` — "What's Working NOW" section, changelog
- `02-LinkedIn-Algorithm/Format-Performance-Data.md` — if new benchmarks
- `02-LinkedIn-Algorithm/Posting-Time-Guidelines.md` — if new data

### 1.2 Viral Trends Refresh

**What to check:**
1. Authors watchlist from `03-Viral-Trends/Viral-Trends-Watchlist.md` — new posts
2. Trending formats on LinkedIn
3. New hook patterns that are gaining engagement
4. What has started to die / saturate

**What to update:**
- `03-Viral-Trends/Current-Trends.md` — HOT NOW / RISING / DECLINING / DEAD
- `03-Viral-Trends/Hook-Pattern-Library.md` — if new formulas
- `03-Viral-Trends/Anti-Patterns.md` — if new dead patterns

### 1.3 Output

A short summary: "What changed in the algorithm and trends this week" — deliver as a message to the user.

---

## TASK 2: Content Scan — new author materials (Wednesday)

### 2.1 Scan for new transcripts

Check every transcript folder for NEW files (after the date of the last scan):

**Where to look (full list):**

```
# General transcripts
your-transcripts/synced-meetings/
your-transcripts/marketing-meetings/
your-transcripts/webinars/
your-transcripts/strategy-calls/
your-transcripts/internal-product-calls/

# Podcasts and interviews
your-raw-sources/podcasts-and-events/
your-transcripts/marketing-meetings/Podcast and Interview Calls/

# Conferences and streams
Media activities/Cursor Case Activities/Conferences/
Media activities/Cursor Case Activities/Livestreams/
Media activities/Partnership-Activities/

# Client / project calls
Production/Projects/Projects list/*/Meetings transcripts/
Sales/Presales/Projects/Projects list/*/Transcripts/

# Telegram and external sources
your-raw-sources/telegram-posts/
your-raw-sources/external-references/
your-raw-sources/media/
```

### 2.2 Identify the author

For each new file:
1. Who is the main speaker? (by name in the filename or content)
2. Which Expertise Cluster does the content belong to?
3. Are there any new:
   - Stories (cases, anecdotes, examples)
   - Speech patterns (new signature phrases)
   - Frameworks (new models/approaches)
   - Contrarian positions
   - Metrics/numbers

### 2.3 Output

For each author with new materials:
- "Found X new transcripts/files for [Author]"
- "Key new insights: [list]"
- "Recommendation: update DIP sections [list of sections]"
- "Potential post topics: [list]"

### 2.4 Update the DIP (if needed)

If significant new materials are found:
1. Load `_DIP-Update-Workflow.md`
2. Update the relevant DIP sections
3. Add entries to the Source Index and Update Log

### 2.5 Auto-populate the Topic Backlog

After scanning the transcripts (steps 2.1–2.3) — extract potential post topics.

**For each new transcript:**
1. Identify the author (main speaker)
2. Extract 1–3 ideas for posts (specific story, case, opinion, framework)
3. Record each idea in `Posted/[Author]/Topic-Backlog.md` → **Inbox**

**Entry format:**
```
| - [ ] | [short description + hook framing] | [source: filename] | [date] |
```

**Rules:**
- Check for duplicates: don't add if the topic is already in Inbox/Prioritized/In Progress/Done
- Don't add general/abstract ideas — only specific ones: with numbers, cases, stories
- Each topic is tied to the author's DIP Expertise Cluster
- Specify the source (path to the transcript) for later post creation

---

## TASK 3: Post Performance Review (Friday)

### 3.1 Collect metrics

For each post published this week:
1. Collect impressions, likes, comments, saves, shares
2. Update `05-Format-Testing/Performance-Log.md`
3. Update the frontmatter in the post file (Post-Publication section)

### 3.2 Pattern analysis

- Which formats performed best?
- Which hooks drove more "See more" clicks?
- Which topics resonated?
- Any surprises (a good post didn't take off, or vice versa)?

### 3.3 Update the Experiment Backlog

- Close completed experiments
- Add new hypotheses based on results
- Update `05-Format-Testing/Experiment-Backlog.md`

### 3.4 Next Week Planning

- Which authors are publishing next week?
- Which topics are in the queue?
- Are there events/webinars we can turn into content?
- Cross-team coordination: who publishes what, to avoid overlap

### 3.5 Feedback Log Review

Check the Feedback Log (section 11) in each author's DIP:

1. Scan `[Author]-DIP.md` → "FEEDBACK LOG & LEARNINGS" section
2. If a feedback category repeats **3+ times** (the same theme: tone fix, wrong word, format issue):
   - **Promote to core DIP** — move from the Feedback Log to the appropriate section:
     - Tone of Voice → "They NEVER say" / "Speech Patterns"
     - Format issue → "Format Preferences"
     - Content angle → "Editorial Rules" / "Viral Angles"
   - Mark in the Feedback Log: `[PROMOTED → Section X, YYYY-MM-DD]`
3. If feedback is one-off — leave it in the Feedback Log; it may repeat later

---

## How to run it

The user says one of:
- "Weekly update" / "Weekly refresh"
- "Refresh algorithm" / "Algorithm refresh"
- "Scan new materials" / "Content scan"
- "Performance review" / "Posts performance review"

Claude loads this document and executes the corresponding TASK.

---

## Changelog

| Date | What Changed |
|------|-------------|
| 2026-02-23 | Added Step 2.5 (auto-populate Topic Backlogs) and Step 3.5 (Feedback Log review) |
| 2026-02-19 | Initial version created |

---

*This workflow is updated when folder structures change or new content sources are added.*
