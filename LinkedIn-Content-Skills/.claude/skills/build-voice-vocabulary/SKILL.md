---
name: build-voice-vocabulary
description: Builds a Voice Vocabulary for an author — a dictionary of their characteristic phrases, turns of speech, fillers, metaphors, and contrarian formulas. Used as a humanization layer on top of the DIP. Collected ONLY from raw sources (transcripts, voice input, personally written Telegram posts), NEVER from the author's LinkedIn posts.
disable-model-invocation: true
argument-hint: [Author]
allowed-tools: Read, Grep, Glob, Edit, Write
---

# Build Voice Vocabulary

> Voice Vocabulary is a layer on top of the DIP (Digital Identity Profile), specifically for humanizing the final draft of a post. The DIP describes tone and topics. Voice Vocabulary provides verbatim phrases from the author that you can use as targeted replacements for AI markers.

## When to invoke

- After the author has a DIP at v0.7+ (3+ transcripts in `_Sources/`).
- On the first humanization attempt — when it becomes clear that DIP quotes aren't enough.
- Every 3 months — refresh with new transcripts.

## Pipeline (8 steps)

### Step 1: Collect source list

Read everything available about the author:

- Transcripts of calls, podcasts, interviews where the author is a speaker
- Voice input (if audio logs exist)
- Telegram posts personally written by the author (not reposts)
- Internal meetings where the author talks a lot live (NOT a Granola summary — you need the full transcript)
- The author's CV, articles (only if written by them, without AI)

**❌ Do NOT use:**

- The author's LinkedIn posts (even their own) — that's OUTPUT, feedback loop = voice degradation
- AI-generated content, even if the author approved it
- Other people's posts "in the author's style"
- Transcripts where the author only reacts to others (chat comments during someone else's talk)

### Step 2: Spin up the template

Copy `Templates/Voice-Vocabulary-Template.md` → `Knowledge-Base/01-Identity-Profiles/_Voice-Vocabulary/[Author]-Voice-Vocabulary.md`.

Fill the frontmatter (author, sources, language coverage, status: v0.1 initial).

### Step 3: Extract Sentence Starters

Read each transcript. Find **recurring** sentence openings (5+ times for high, 3–5 for medium, 1–2 for low).

Record in this format:

```text
| Phrase | Frequency | Example (with source) | When to use |
| "I think I figured out..." | high (10+) | "I think I figured out how to give agents access..." — TG 2026-02-16 | Hedged claim setup |
```

Start with high-frequency patterns (10+). Then medium. Skip low — it's not a pattern.

### Step 4: Idiomatic Phrases

Personal turns of phrase that are recognizable as this author. Often — short 2–4-word expressions with characteristic flavor.

Test: "if I heard this phrase from behind a wall, would I know it's [Author]?"

### Step 5: Filler Words / Tics

Filler words in spoken speech. **Important:** use them carefully in LinkedIn posts — 1 per post, no more. They work as a micro-signal of live speech, but oversaturation becomes irritating.

### Step 6: Categories 4–9

Same approach for:

- Characteristic Adjectives & Verbs
- Code-Switching Patterns (if the author is multilingual)
- Numbers & Scale References (how they handle numbers)
- Recurring Metaphors (metaphors with repetition — NOT one-offs)
- Contrarian Move Formulas (formulas like "everyone thinks X, in reality Y")
- Closing Patterns (how they wrap up a thought)

### Step 7: Sources section

At the end of the file — a table of all source files with type and date. This lets you:

- Update properly as new transcripts appear
- See which category is under-sampled (e.g., only 1 EN source → English coverage is weak)

### Step 8: Status + What's NOT covered

In the footer, set the `status` (v0.1 / v0.5 / v0.7 / v1.0) and the "Not Covered / TBD" block:

- Categories with insufficient entries
- Hypotheses to verify against future transcripts
- Questions for the author

## Validity checklist

After completing the first pass, walk through the checklist:

- [ ] Minimum 3–5 entries in each main category (1–4, 9)?
- [ ] Every entry has a verbatim quote + source ref?
- [ ] Frequency is correctly assigned (not "high" for everything)?
- [ ] At least 5 distinct files covered in Sources?
- [ ] No entries from the author's LinkedIn posts (raw sources only)?
- [ ] Frontmatter fully filled?
- [ ] Status is accurate (if you only have 3 sources → v0.5, not v1.0)?

If it fails on ≥2 items — that's v0.5 (working), not v1.0.

## Anti-patterns

- ❌ Rebuilding the DIP inside the Voice Vocabulary — overlapping work.
- ❌ Taking "unique" words from a single transcript as a pattern — that's noise, not signal.
- ❌ Including phrases the author used in their first-ever public talk — they may sound unnatural there.
- ❌ Auto-generating from posts — that produces a feedback loop and loss of voice.

## Output

A file at `Knowledge-Base/01-Identity-Profiles/_Voice-Vocabulary/[Author]-Voice-Vocabulary.md`, ready for use by `/detect-ai` and `/check-generic` validators as a reference for humanization replacements.
