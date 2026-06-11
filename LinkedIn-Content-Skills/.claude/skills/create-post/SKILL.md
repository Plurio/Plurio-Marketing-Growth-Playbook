---
name: create-post
description: Creates a LinkedIn post for a team author. Use when the user asks to write, create, or make a LinkedIn post, or says "turn this into a post", "write a post about...", "[Author] wants to write about...".
disable-model-invocation: true
argument-hint: [Author] [topic or source material]
allowed-tools: Read, Grep, Glob, Edit, Write, Bash(python *), Skill(validate-post *)
---

# Create LinkedIn Post

Create a LinkedIn post for an author using the full 8-step pipeline.

## Input

- `$0` — author name (Seva, Kirill)
- Remaining arguments or conversation context — topic, source, voice input

## Required files to load

Before starting, load:

1. **Author DIP** (required):
   `Knowledge-Base/01-Identity-Profiles/[Author]-DIP.md`
   - Mapping: Seva → Seva-Ustinov-DIP.md, Kirill → Kirill-Kasimskiy-DIP.md

2. **Author Voice Vocabulary** (required if the file exists):
   `Knowledge-Base/01-Identity-Profiles/_Voice-Vocabulary/[Author]-Voice-Vocabulary.md`
   - Contains the author's characteristic phrases from their transcripts and Telegram (NOT from published posts).
   - Used for humanization: in Step 4 when writing the body, prefer phrasing from the Voice Vocabulary over generic LinkedIn formulations.
   - If a Voice Vocabulary file for the author doesn't exist yet — proceed without it, but in the final report note "Voice Vocabulary for [Author] not created".

3. **Post-Creation-Engine** (required):
   `Knowledge-Base/04-Post-Creation-Engine/Post-Creation-Engine.md`

4. **Algorithm-Intelligence** (required):
   `Knowledge-Base/02-LinkedIn-Algorithm/Algorithm-Intelligence.md`

5. **AI-Detection-Reference** (required — for understanding 360Brew penalties):
   `Knowledge-Base/02-LinkedIn-Algorithm/AI-Detection-Reference.md`

6. **Current-Trends** (recommended):
   `Knowledge-Base/03-Viral-Trends/Current-Trends.md`

7. **Hook-Pattern-Library** (when picking a hook):
   `Knowledge-Base/03-Viral-Trends/Hook-Pattern-Library.md`

8. **Benchmark-Validation-System** (if the post will contain numbers):
   `Knowledge-Base/04-Post-Creation-Engine/Benchmark-Validation-System.md`

## Pipeline

### Step 0: Fresh Scan — refresh the DIP before working (MANDATORY)

**CRITICAL PRINCIPLE:** The DIP is built ONLY from transcripts and recorded speech. Posts are OUTPUT, not INPUT.

Before creating a post:
1. Open the author's DIP → check `Last Updated` and `Last Fresh Scan`
2. Find ALL new transcripts featuring the author after that date (sources — see the Source Map in CLAUDE.md)
3. Quickly scan each new transcript (5 min/file): new positions, stories, numbers, phrases
4. If something material is found → update the DIP before writing the post
5. Update the `Last Fresh Scan` date in the DIP

Run **Steps 1–7** from Post-Creation-Engine.md. In brief:

### Step 1: Identify the author and load the DIP
Extract from the DIP: Tone of Voice, Expertise Clusters, Stories Bank, Viral Angles, Format Preferences, "They NEVER" list.

### Step 2: Extract the core message
One key idea. If multiple → propose a series. Classify by cluster and pillar from the DIP.

### Step 3: Pick angle and format
- Angle: from DIP Viral Angles + Current-Trends.md
- Format: from Algorithm-Intelligence.md + DIP Format Preferences
- Check Anti-Patterns.md so you don't repeat dead patterns

### Step 4: Write the post
- Hook: use Hook-Pattern-Library.md, adapt to the author's tone, 2–3 variants
- Body: short paragraphs, examples from DIP Stories Bank, first person (I/my)
- **Voice Vocabulary integration:** when writing the body, where the author already has a similar thought in the Voice Vocabulary (Sentence Starters, Idiomatic Phrases, Characteristic Adjectives/Verbs, Metaphors, Closing Patterns), prefer their phrasing over generic phrasings. Don't stuff in tics for the sake of count — point-swap generic phrases for authentic ones.
- CTA: specific, tied to the goal of the post (NOT "Agree?" / "Thoughts?" / 🔥)
- Length: sweet spot 1,200–1,800 characters
- **What NOT to do (see detect-ai Levels 4F–4I):** A-vs-B opener in the first 3 lines, false-vulnerability openers ("I'll be honest..." / "Hot take:"), "three lessons" numbered list in the closing, generic motivational CTAs, "one sentence per line + blank line between" carousel pattern longer than 5 lines in a row.

### Step 5: Validation (built-in)
Run the basic check from Post-Creation-Engine.md Step 5. Full validation comes in the next step.

### Step 6: Format output
1. Post text (copy-paste ready)
2. Alternative hooks (2–3 variants with notes)
3. Format recommendation (if visuals/carousel/video are needed — description)
4. Publish recommendation (day/time, coordination with other authors)
5. Source attribution (what came from which transcript/document)

### Step 7: Save draft
- Path: `Posted/[Author]/YYYY-MM-DD-[slug].md`
- Format: per the template `Knowledge-Base/04-Post-Creation-Engine/Post-Template.md`
- Required: fill `source_refs:` in the frontmatter — list of ALL sources used

## Step 8: VALIDATION

After saving the draft, run full validation:

`/validate-post [path to the created file]`

This runs:
- Fact-checking (`/check-facts`)
- Generic / repetition check (`/check-generic`)
- Source map (`/check-sources`)
- Final checklist (characters, format rotation, cluster, hook, anti-patterns, algorithm, mobile)

Show the user a summary validation report.

## Step 9: Feedback (after any incoming feedback)

After EVERY piece of feedback from the author/team → update the DIP:
- "FEEDBACK LOG & LEARNINGS" section
- Format: Date | Post | Category | Feedback | Lesson Learned
- Categories: tone | accuracy | context | angle | format | strategy

## Rules

- **One post = one file.** When reworking, overwrite the current file, do NOT create -v2, -v3
- **First person.** ALWAYS I/my in personal posts. NEVER we/our
- **Fact-based.** Every claim is backed by real data from sources
- **Don't invent.** Don't make up stories — use only the DIP Stories Bank and real sources
- **Coordination.** Check `Posted/*/` for the past week — avoid topic overlap with other authors
