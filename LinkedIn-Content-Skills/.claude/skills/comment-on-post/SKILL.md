---
name: comment-on-post
description: Writes a LinkedIn comment on SOMEONE ELSE's post on behalf of an author. Loads the author's DIP, analyzes the post, picks a formula, and checks source grounding. Use when you need to comment on another person's post.
disable-model-invocation: true
argument-hint: [Author]
allowed-tools: Read, Grep, Glob
---

# Comment on Someone's Post

Write a comment on someone else's LinkedIn post on behalf of an author.

## Comments are NOT posts (the core principle)

Adrian Vega's 500-post study + the LinkedIn 360Brew penalty: a comment that sounds like a mini-post is flagged by the algorithm as automation / AI spam. Symptoms of a bad comment:
- Post structure: hook → body → CTA
- Multiple paragraphs
- Em dashes, jagged rhythm, lists
- "Three insights:" / "Here's the thing:"
- Ends with a question (an AI marker and bad tone)

A good comment sounds like a chat reaction:
- 1–3 sentences, ONE thought
- A concrete reply to a concrete point in the original post
- Can be grammatically loose (fragments, no period at the end)
- Does NOT end with a question
- Optionally: a meme, an image, a short reaction
- Can start with a lowercase letter or a conjunction ("and yeah, ...", "but at the same time...")

## Voice Vocabulary in comments

Filler words and tics from `_Voice-Vocabulary/[Author]-Voice-Vocabulary.md` ("Filler Words / Tics" and "Sentence Starters") are used in COMMENTS more than in posts — a comment is closer to spoken speech. This is what makes the comment recognizable as the author rather than a generic LinkedIn blob.

Do not use in comments:
- Voice-only markers explicitly flagged in the Voice Vocabulary as "not for posts" (e.g., "well there", "y'know" — spoken speech, not written)
- AI markers from `detect-ai/SKILL.md` Level 4F/4G/4H/4I (A-vs-B, false vulnerability, three lessons, generic CTA)

Reference: `Knowledge-Base/02-LinkedIn-Algorithm/AI-Detection-Reference.md`

## Input

- `$0` — author name (Seva, Kirill, Plurio)
- Conversation context — text/link to the post being commented on

## Required files

1. **Author's DIP:**
   `Knowledge-Base/01-Identity-Profiles/[Author]-DIP.md`
   - Mapping: Seva → Seva-Ustinov-DIP.md, Kirill → Kirill-Kasimskiy-DIP.md, Plurio → Plurio-AI-DIP.md

2. **Comments Engine:**
   `Knowledge-Base/06-Comments-Engine/Comments-Engine.md`

## Pipeline

### Step 1: Load DIP

Extract from the DIP:
- Tone of Voice + Speech Patterns
- "They NEVER" — forbidden patterns
- Expertise Clusters — topics the author can speak to authoritatively
- Stories Bank — concrete cases and facts for grounding

### Step 2: Post analysis

1. Read the original post
2. Determine:
   - What is the post about? Which expertise cluster does it match?
   - Is there room to add a unique perspective?
   - What tone is appropriate? (serious, light, provocative)
   - If the topic is OUTSIDE the author's clusters — warn the user

### Step 3: Pick a formula

From the Comments Engine, Type 2 (comment on someone else's post):

| Situation | Formula |
|-----------|---------|
| Add your own experience | "We did something similar + [result]" |
| Clarify / extend | "This + [missing piece]" |
| Ask a smart question | "Curious about [specific aspect]" |
| Contrarian take | "Interesting — our data shows [different]" |

### Step 4: Write the comment

**Rules:**
- Minimum 15 words (for the 2.5× algorithmic weight)
- Optimal 30–80 words
- First person (I/my)
- Specifics from the DIP Stories Bank
- No hashtags
- No emoji (unless the author uses them in the DIP)
- Tone = DIP, but slightly softer (we're a guest here)

### Step 5: Source Grounding

For EACH factual claim in the comment:

| Category | Action |
|----------|--------|
| **Verified fact** — has a concrete source | Keep |
| **Grounded inference** — direct consequence of verified facts | Keep, don't embellish |
| **Thin ground** — author's topic but no concrete case | Rephrase: question or known fact |
| **Bullshit** — sounds plausible but invented | Remove or replace with a question |

**Red flag:** >50% of claims are thin ground / bullshit → rewrite.

### Step 6: Validation

- [ ] Sounds like the author? (DIP tone check)
- [ ] Adds value? (not an empty comment)
- [ ] 15+ words?
- [ ] No forbidden patterns from DIP "They NEVER"?
- [ ] First person?
- [ ] Not selling or pitching?
- [ ] Doesn't duplicate the original post's content?
- [ ] No "not X but Y" constructions?
- [ ] No "I've seen..." without specifics?
- [ ] No generic validation ("Great post!", "So true!", "This is the shift")?
- [ ] Source grounding passed?
- [ ] **Doesn't sound like a mini-post** (no hook→body→CTA, no multiple paragraphs)?
- [ ] **Does NOT end with a question**?
- [ ] **Uses Voice Vocabulary elements** (author's fillers/tics, where appropriate)?
- [ ] No AI markers detect-ai Level 4F–4I (A-vs-B opener, false vulnerability, three lessons, generic CTA)?

## Output

Return:
1. **Comment** — ready-to-publish text
2. **Source grounding table** — each claim → source → category
3. **Alternative variant** — a different angle/formula (if appropriate)

## Anti-Patterns (FORBIDDEN)

- "Great post!" / "Love this!" / "So true!"
- Quoting a line from the post + "this is the line/shift/key"
- Echoing metrics/phrases from the post back to the author
- "I've seen..." / "I've watched..." without specifics
- "not X but Y" constructions
- Transformational pivots ("it stops being X and becomes Y")
- Self-promotion on someone else's post
- "That's exactly how we designed it" and variants
- Selling/pitching in comments
