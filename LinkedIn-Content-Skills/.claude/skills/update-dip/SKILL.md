---
name: update-dip
description: Updates an author's Digital Identity Profile with new data from transcripts. Use when a DIP needs to be refreshed after a new transcript, feedback, or a scheduled review. IMPORTANT: the DIP is built ONLY from transcripts and recorded speech, NEVER from posts.
disable-model-invocation: true
argument-hint: [Author]
allowed-tools: Read, Grep, Glob, Edit
---

# Update Digital Identity Profile

Refresh an author's DIP with new data from transcripts and recorded speech.

## CRITICAL PRINCIPLE

The DIP is built ONLY from source material — transcripts, meeting recordings, talks, podcasts. **NEVER from posts.** Posts are OUTPUT of the DIP, not INPUT. Building the DIP from posts → feedback loop → loss of the real voice.

## Input

- `$0` — author name (Seva, Kirill)
- Conversation context — a new transcript, feedback, or a scheduled-update request

## Required files

1. **Current author DIP:**
   `Knowledge-Base/01-Identity-Profiles/[Author]-DIP.md`

2. **DIP Update Workflow:**
   `Templates/DIP-Update-Workflow.md`

## Data sources (hierarchy)

| Priority | Source | Path |
|----------|--------|------|
| 1 | Podcasts and talks | `your-raw-sources/podcasts-and-events/` |
| 2 | Conferences | `Media activities/Cursor Case Activities/Conferences/` |
| 3 | Livestreams | `Media activities/Cursor Case Activities/Livestreams/` |
| 4 | AGI/Product calls | `your-transcripts/internal-product-calls/` |
| 5 | Presales calls | `Presales/Projects/Projects list/*/Transcripts/` |
| 6 | Marketing calls | `your-transcripts/marketing-meetings/` |
| 7 | AI positioning calls | `your-transcripts/strategy-calls/` |
| 8 | Client calls | `Production/Projects/Projects list/*/Meetings transcripts/` |
| 9 | Granola syncs | `your-transcripts/synced-meetings/` |
| 10 | Webinars | `your-transcripts/webinars/` |
| 11 | Telegram (the author's own words) | `your-raw-sources/telegram-posts/` |

**NOT sources:** LinkedIn posts (`Posted/`), PR comments, presentations, marketing copy, product blurbs.

## Pipeline

Follow the process from _DIP-Update-Workflow.md.

### Three update types:

**1. New transcript / material:**
- Read the new transcript — focus ONLY on the author's speech
- Extract: new stories, speech patterns, frameworks, contrarian positions, metrics, numbers
- Check for contradictions with the current DIP (the person may have changed their mind)
- Update the relevant DIP sections (Stories Bank, Frameworks, Expertise Clusters, Tone of Voice)
- Update the Source Index
- Add an entry to the Update Log

**2. Feedback (from the author personally):**
- Record it in the "FEEDBACK LOG & LEARNINGS" section
- Format: Date | Context | Category | Feedback | Lesson Learned
- Categories: tone | accuracy | context | angle | format | strategy
- If a pattern repeats 3+ times → promote it from the Feedback Log to the main DIP sections

**3. Fresh Scan (before creating content):**
- Check `Last Updated` and `Last Fresh Scan` in the DIP
- Find ALL new transcripts featuring the author after that date
- Quickly scan each (5 min/file): new positions, stories, numbers, phrases
- If there are material updates → update the DIP before content
- Update the `Last Fresh Scan` date

**4. Quarterly review:**
- Audit every section for accuracy
- Compare against the 2–3 most recent transcripts — does the voice still match?
- Verify: are there unprocessed transcripts?
- Update metrics (team size, clients, numbers)
- Increment the version in the Update Log
