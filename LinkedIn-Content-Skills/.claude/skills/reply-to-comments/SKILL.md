---
name: reply-to-comments
description: Replies to comments under the author's OWN LinkedIn post. Batch mode: processes multiple comments at once with phrasing variety. Critical for the algorithm — replying within the first 30 minutes = +64% comments.
disable-model-invocation: true
argument-hint: [Author]
allowed-tools: Read, Grep, Glob
---

# Reply to Comments on Own Post

Generate replies to comments under the author's own post. Batch mode with phrasing rotation.

## Input

- `$0` — author name (Seva, Kirill, Plurio)
- Conversation context — text of the comments to reply to (one or many)

## Required files

1. **Author DIP:**
   `Knowledge-Base/01-Identity-Profiles/[Author]-DIP.md`

2. **Comments-Engine:**
   `Knowledge-Base/06-Comments-Engine/Comments-Engine.md`

## Why this is critical

| Fact | Impact |
|------|--------|
| Author replies within the first 30 min | +64% total comments, 2.3× views |
| Thoughtful reply (15+ words) | 2.5× algorithmic weight |
| Every reply = a new signal | The algorithm recomputes reach |

## Pipeline

### Step 1: Load DIP + the original post

- Author DIP → Tone of Voice, Speech Patterns, Stories Bank
- Original post (if available) → context for the replies

### Step 2: Classify the comments

For each comment, identify the type:

| Type | Reply formula |
|------|---------------|
| **Agreement / support** | Expand + Add layer: "And what most people miss is [deeper insight]" |
| **Question** | Answer + Bridge: "Short answer: [X]. Real answer: [nuance]" |
| **Disagreement** | Acknowledge + Reframe: "I see your point, but [counter-evidence]" |
| **Compliment** | Redirect to insight: "The real credit goes to [specific detail]" |
| **"How can I learn more?"** | Give value + soft CTA: "Here's what I'd start with: [tip]" |
| **Congratulations** | From the micro-reply bank (rotate!) |

### Step 3: Write replies (batch)

**Rules for EVERY reply:**
- Minimum 15 words for substantive comments
- First person (I/my)
- Specifics from the DIP
- Source grounding: every claim is traceable

**Rotation rule (CRITICAL):**
- Do NOT repeat the same formula across different comments
- Alternate: words → emoji → forward-looking → warm → playful
- If 10+ congratulations: 3–4 can be emoji, the rest — words
- NEVER two identical replies in a row

**Bank of micro-replies for congratulations:**

Energetic:
- "Buckle up — this is just the beginning"
- "The fun part starts now"
- "This is just chapter one."
- "We're just warming up."

Warm:
- "Means a lot 🙏"
- "Appreciate you!"
- "This made my day."

With character:
- "Not gonna lie — feels good."
- "Now the real work begins 💪"

Minimal:
- "🙏" / "🚀" / "💪" / "❤️🔥"

### Step 4: Validate each reply

- [ ] Sounds like the author?
- [ ] Adds value (not empty)?
- [ ] Doesn't repeat the previous reply's formula?
- [ ] First person?
- [ ] Source grounding (for substantive replies)?
- [ ] Doesn't echo the post content back?

### Step 5: Cross-team amplification (if applicable)

If teammates appear among the commenters, the reply should:
- Address them directly (2nd person: "you're building...")
- NOT self-promote
- Add the author's unique angle

## Output

For each comment:

```markdown
**Comment from [name]:** "[text]"
**Type:** [agreement / question / disagreement / compliment / congratulations]
**Reply:** [reply text]
**Formula:** [which formula was used]
```

At the end — a summary:
- Total replies: [N]
- Formulas used: [list without repeats]
- Timing recommendation: [when to publish]
