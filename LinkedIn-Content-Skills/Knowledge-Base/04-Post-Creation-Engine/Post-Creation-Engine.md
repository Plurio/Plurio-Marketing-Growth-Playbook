# Post Creation Engine

> Main workflow for creating LinkedIn posts.
> This document is the instruction Claude follows when creating a post for any author.

---

## TRIGGER

When the user says one of:
- "Create a post for [Author]"
- "Turn this into a post" (with voice input or text)
- "Write a LinkedIn post about [topic]"
- "[Author] wants to write about [topic]"
- Voice input + any post request

---

## STEP 1: Identify the author and load the DIP

1. Identify which author the post is being created for
2. Load their DIP: `Skills/01-Digital-Identity-Profiles/[Author]-DIP.md`
3. If the DIP does not exist → suggest creating it via `_DIP-Creation-Workflow.md`
4. Memorize the essentials:
   - Tone of Voice (how to write)
   - Expertise Clusters (what to write about)
   - Stories Bank (examples to use)
   - Viral Angles (which angles work)
   - Format Preferences (which formats fit)
   - "They NEVER" list (what to avoid)

---

## STEP 2: Extract the core message from the input

From the voice input / transcript / topic description, extract:

### 2.1 One key idea
What is the SINGLE main takeaway? If there are multiple ideas → split into multiple posts and propose a series.

### 2.2 Classification
- Which **Expertise Cluster** does it belong to? (from the DIP)
- Which **Editorial Pillar** does it serve? (from the DIP)
- Who is the **target reader**? (from the DIP Audience)

### 2.3 If unclear
Ask the author: "What is the one takeaway you want the reader to leave with?"

---

## STEP 3: Choose angle and format

### 3.1 Angle Selection

1. Check **DIP Viral Angles** → which signature angle fits?
2. Check **`03-Viral-Trends/Current-Trends.md`** → is there a trending angle that would amplify this?
3. Check **`03-Viral-Trends/Anti-Patterns.md`** → does the idea fall into an overused pattern?
4. Check **[`Marketing-Intelligence/Hook-Bank.md`](../../../../Marketing-Intelligence/Hook-Bank.md)** → ready-made hooks by persona and awareness level (60+ hooks + 20 marketing angles)

### 3.2 Format Selection

1. Check **`02-LinkedIn-Algorithm/Algorithm-Intelligence.md`** → which formats are currently performing?
2. Check **DIP Format Preferences** → what fits this author?
3. Check **`05-Format-Testing/Experiment-Backlog.md`** → is there a planned experiment?
4. Recommend a format with rationale

**Quick format selection matrix:**

| Content type | Recommended format |
|-------------|---------------------|
| Hot take / opinion | Text only (emotion carries it, visuals dilute) |
| Framework / how-to | Carousel (save-worthy, high dwell time) |
| Data insight | Text + infographic |
| Personal story | Text only or Text + authentic photo |
| Client case study | Carousel or Text + image |
| Product demo | Video or Carousel |
| Behind the scenes | Video (short, <60 sec) |

---

## STEP 3.5: Suggest a reference (optional)

Ask the author:

> "Want to anchor on one of our external references? We have a library of posts with strong framing frameworks — for example, a value-first product story (describing a product through value, not features)."

If the author says **yes**:
1. Load `04-Post-Creation-Engine/Reference-Posts-Library.md`
2. Suggest references that fit the current topic (with a short framework description)
3. The author picks → adapt the **structure and device** to their topic and DIP
4. Content and facts come ONLY from the author's canonical sources

If the author says **no** or **skip** → proceed to STEP 4.

**When NOT to suggest:** hot takes, personal stories, posts where the author has already specified the exact format.

---

## STEP 4: Write the post

### 4.1 Hook (first 2 lines)

**Rules:**
- Only the first ~140 characters are visible before "See more" — this is the most valuable territory
- First line → pause (double line break) → second line
- The hook must STOP the scroll
- **360Brew "Lost-in-Distance" effect:** The first sentence gets disproportionate attention weighting from the algorithm. A generic/vague prologue → deprioritization BEFORE people even scroll

**Process:**
1. Load formulas from **`03-Viral-Trends/Hook-Pattern-Library.md`**
2. Adapt to the author's tone from the DIP (Personalized Hook Formulas)
3. Write 2–3 hook variants
4. Check: "If I saw this in the feed, would I stop? Or scroll past?"

### 4.2 Body

**Tone rules (from the DIP):**
- Write in the author's speech patterns (DIP Speech Patterns)
- Use the author's signature phrases
- Do not use banned patterns (DIP "They NEVER")
- First person: "I/my" — NEVER "we/our" in personal posts (exception: the author themselves writes "we" about the team)

**Body structure:**
- Short paragraphs (1–3 lines)
- One idea per paragraph
- Concrete examples from the DIP Stories Bank
- Specific numbers beat abstract claims
- If there is a framework → give the steps (numbered list)

**Structure formulas (pick one):**
- **PAS**: Problem → Agitation → Solution
- **BAB**: Before → After → Bridge
- **AIDA**: Attention → Interest → Desire → Action
- **Story Arc**: Hook → Context → Conflict → Resolution → Lesson

### 4.3 CTA (Call to Action)

**Rules:**
- No generic CTAs ("What do you think?", "Agree?")
- The CTA must be specific and inviting
- Match the CTA to the goal:
  - Want comments → ask a provocative question on the topic
  - **Want saves (PRIORITY — saves = 5–10x like)** → use a Save CTA (see below)
  - Want shares → "Share with someone who [specific situation]"
  - Want DMs → "DM me [specific word] and I'll send you [specific thing]"

### 4.3.1 Save CTAs — when and which to use

**Why it matters:** Saves are the strongest signal for the algorithm (5–10x like). A Save CTA is not appropriate in every post, but in certain content types it delivers a significant reach boost.

**When to add a Save CTA:**

| Content type | Appropriate? | Why |
|-------------|----------|--------|
| Framework / how-to / checklist | **YES — always** | People genuinely return to step-by-step instructions |
| Carousel with actionable steps | **YES — always** | Carousel + save = best combination in 2026 |
| Data insight / benchmark | **YES** | Reference material people come back to |
| Tool / resource list | **YES** | Utility content = high save rate |
| Personal story / vulnerability | **NO** | A Save CTA breaks the emotional moment. Better: a discussion question |
| Hot take / contrarian | **NO** | A provocation needs a comment CTA, not a save |
| Behind-the-scenes / build in public | **Depends** | If there is an actionable takeaway — yes. If it's a pure story — no |
| Announcement (conference, podcast) | **NO** | Announcements are not save-worthy; share CTA is better |

**Save CTA formulas (adapt to the author's voice from the DIP):**

| Formula | When to use | Example |
|---------|-------------------|--------|
| "Save this for when you [specific situation]" | Framework, how-to | "Save this for when you need to kill underperforming creatives fast" |
| "Bookmark this — you'll need it when [context]" | Reference material, data | "Bookmark this — you'll need it when planning your next creative test" |
| "Save → come back when you're [doing X]" | Step-by-step guide | "Save → come back when you're setting up your first AI agent workflow" |
| "This is one of those posts you'll want to find later" | Comprehensive framework | "This is one of those posts you'll want to find later. Save it." |
| "Keep this for your next [X]" | Template, checklist | "Keep this for your next campaign audit" |
| "[Just at the end of the post, no CTA phrase]" + value density | When the post is so useful that saves happen organically | No explicit CTA needed — the framework is save-worthy on its own |

**Rules:**
- **Not in every post.** A Save CTA in a hot take or personal story feels unnatural. Use it only when the content is genuinely reference-worthy
- **Don't make save the only CTA.** You can combine: save CTA + discussion question. For example: "Save this framework. And tell me — what's your current rule for killing creatives?"
- **Adapt to the author.** Seva would more likely say a neutral "Bookmark this." Kirill might say "You'll want this when you're scaling next campaign"

### 4.4 Length

- **Sweet spot: 1,200–1,800 characters** (+47% engagement vs other lengths)
- Short posts (<500 characters): only for bold statements, hot takes
- Long posts (1,800–3,000): only for story-driven content with a strong hook

---

## STEP 5: Validation

Run the post through the checklist:

### Algorithm Check
- [ ] Does the topic match the author's LinkedIn headline? (Profile-Content Alignment — 360Brew cross-checks)
- [ ] Is the post within the author's 3–4 core topics? (Topic Consistency — ~90 days for semantic authority)
- [ ] Is the first sentence a concrete anchor (not generic)? (360Brew "Lost-in-Distance" effect)
- [ ] Is the structure readable (short paragraphs, whitespace)? (Helps 360Brew parse semantics)
- [ ] No links in the post? (~60% reach penalty). If there is one — after ~300 characters
- [ ] Is there a CTA and is it specific?
- [ ] Hashtags: 1–3 max (not 5+; 360Brew does not need them for topic classification)
- [ ] Is the content save-worthy? (Saves = 5–10x like by weight)

### Tone Check
- [ ] Does it sound like the author? (compare against DIP Speech Patterns)
- [ ] No generic phrases from the DIP "They NEVER" list?
- [ ] First person (I/my), not "we/our"?
- [ ] Would the author recognize themselves in this post?

### Benchmark Check (if there are claims with numbers)
- [ ] Run through `04-Post-Creation-Engine/Benchmark-Validation-System.md`
- [ ] All claims sourced or flagged as opinion

### Differentiation Check
- [ ] No overlap with a recent post by another author on the same topic?
- [ ] Is the author's unique angle visible?

### Anti-Pattern Check
- [ ] Does it not fall into patterns from `03-Viral-Trends/Anti-Patterns.md`?
- [ ] Not "bro-etry" (single-line dramatic paragraphs)?
- [ ] Not engagement bait?
- [ ] Does it not look AI-generated (check for generic phrases)?

### Client Confidentiality Check (if the post is about a client case)

Any post mentioning client data must pass this checklist. Goal — the client must not be identifiable through indirect signals.

**Anonymization levels (apply ALL that are relevant):**

| Data | Forbidden | Allowed |
| ------ | --------- | --------- |
| Company name | Specific client names without permission | "Series B SaaS" / "EdTech company" / "B2C fintech" |
| Budget | Exact figure ("$1.2M/month") | Range ("$500K–$1M/month" or "seven-figure monthly spend") |
| Industry + stage + budget size in one post | All three together — identifiable in 5 minutes | At most two of three |
| Number of clients in one post | 3+ "anonymous" clients with different sizes/industries | 1 client in detail OR an aggregated takeaway without ties to specific cases |
| Metrics the client has not published themselves | Specific conversion rates, LTV, CAC | Relative changes ("3–4x acceleration") |

**When you can name the client:**
- The client has publicly stated their use (e.g., spoke at a webinar)
- There is written permission from the client to mention them
- The client wrote a testimonial and we are using their quote

**Rules for "anonymous" case studies with 2–3 clients:**
- Do not include in one post: (name/alias) + (exact industry) + (exact budget size)
- One of these three parameters must be generalized
- If the case has a unique identifier (the only company in its niche of that size) — add an extra anonymization layer

**Red flag triggers (require extra review):**
- [ ] Do the numbers in the post appear in the client's public sources (press releases, earnings calls)?
- [ ] Is industry + budget size = a unique combination in our portfolio?
- [ ] Does it mention specific product features of the client that identify the company?
- [ ] Does the post contain criticism of the client's process (e.g., "client waited too long")?
  - If yes: extra check — would the client be offended when reading it?

---

## STEP 6: Produce the output

Return to the user:

### 1. Post text (primary)

The finished post, copy-paste into LinkedIn.

### 2. Alternative hooks (2–3 variants)

- **Option A:** [hook] — [why this angle]
- **Option B:** [hook] — [why this angle]
- **Option C:** [hook] — [why this angle]

### 3. Format recommendation

[Recommended format with rationale]

- If carousel → outline of slide content (heading + key thought per slide)
- If video → script outline and recommended duration
- If image → description of the visual direction
- If text+image → description of which image would amplify the post

### 4. Publishing recommendation

- Best day/time (from `02-LinkedIn-Algorithm/Posting-Time-Guidelines.md`)
- Coordination note: if another author recently published on a close topic
- Engagement plan: who to tag, which comments to participate in

### 5. Source attribution

Which transcripts/sources were used (for the post's metadata).

---

## STEP 7: Save the draft

Save the post file to: `Posted/[Author]/YYYY-MM-DD-[slug].md`

Use the format from `04-Post-Creation-Engine/Post-Template.md`.

---

## STEP 7.5: Post-Publication Workflow (REQUIRED)

> Full workflow after publishing: `00-LinkedIn-Master-Skill.md` → PART 4, Section 4.5

**Quick reference — what happens after hitting "Post":**

1. **Minute 0–5:** The author leaves the first comment (Type 3: bonus insight or directing question)
2. **Minute 0–30:** The author comments on 5–10 posts in their niche (+20% reach, +55% profile views)
3. **Minute 0–30:** Booster teammates leave thoughtful comments (15+ words, each with their own angle)
4. **Minute 0–30:** The author replies to EVERY comment (+64% total comments, 2.3x views)
5. **Hour 0–2:** Monitor the Golden Window. DO NOT edit the post
6. **Hour 24–48:** Log performance in `05-Format-Testing/Performance-Log.md`

**When creating the post, also prepare:**
- The author's first comment (Type 3 from Comments-Engine)
- 1 comment from each colleague (cross-team amplification, unique angle)
- Timing: when each comment should appear

---

## STEP 8: Record feedback (REQUIRED)

After EVERY piece of feedback on a post — record it in the author's DIP.

### When to record
- Author or team says "it doesn't sound right", "not my tone", "this is inaccurate"
- They point out a factual error or wrong context
- They ask to change the angle, format, or style
- Any remark that may be useful for future posts

### How to record
1. Open the author's DIP → "FEEDBACK LOG & LEARNINGS" section
2. Add a row to the Log table:
   - `Date`: feedback date
   - `Post`: slug or post name
   - `Category`: `tone` | `accuracy` | `context` | `angle` | `format` | `strategy`
   - `Feedback`: what exactly was said (brief, precise)
   - `Lesson Learned`: the takeaway → what to do differently next time
3. If a pattern repeats 3+ times → promote it to "Patterns" and update the core DIP sections

### Categories
| Category | When to use | Example |
|-----------|-------------------|--------|
| `tone` | Voice/style does not match the author | "Too formal", "That's not his phrase", "Repeating anchor" |
| `accuracy` | Facts are wrong or context is mixed up | "This case isn't about the agent, it's about auto-rules" |
| `context` | Important context or nuance was missed | "Different parts of the webinar = different cases" |
| `angle` | Angle does not fit the audience/product | "Too generic, doesn't land with ICP" |
| `format` | Format doesn't fit | "No carousel needed; text is better" |
| `strategy` | Doesn't fit the strategy/schedule | "This post should be moved after the announcement" |

### Why this matters
- Different team members work with Claude and provide different context
- Feedback accumulates → every next post is better than the previous one
- When creating a new post, Claude MUST reread the author's Feedback Log

---

## Iterations

If the author gives feedback ("doesn't sound right", "not my tone", "add specifics"):
1. Reread the DIP — what was missed?
2. Reread the author's **Feedback Log** — is there a similar prior note?
3. Adapt with the feedback in mind
4. **Record the feedback in the DIP → "FEEDBACK LOG & LEARNINGS" section** (STEP 8)

---

## Coordination between authors

When creating a post, check:
1. What other authors published in the past week → `Posted/*/` (latest files)
2. Whether there is topic overlap
3. **Whether there are repeats of phrases, jokes, punchlines, ideas** from recent posts by THIS SAME author (last 2–4 weeks). If a phrase/idea was already used — DO NOT reuse. Repetition = looks like copy-paste and kills authenticity. Exception: deliberate reinforcement of a catchphrase (discussed explicitly)
4. Whether there is an opportunity for amplification:
   - Author A publishes → Author B comments → 2–3 days later Author B publishes their own angle
   - This creates 3–4 touches on one topic from different perspectives

---

## Content sources: canonical vs derivative

**Canonical sources (INPUT — posts are created from these):**
- Transcripts of meetings, calls, webinars, podcasts
- Documents, articles, interviews by the author
- Telegram posts, voice notes, voice input
- Client calls, presales, product discussions
- External sources (conferences, third-party research, benchmarks)

**Published posts (OUTPUT — we analyze, not source from):**
- `Posted/[Author]/` = already processed content, adapted for LinkedIn
- Used for: performance analysis, tracking topics/formats, avoiding repetition
- NOT used as source material for new posts
- A post is NEVER a canonical source for another post

**Rule:** when creating a new post, always look for raw materials (transcripts, documents, voice input), rather than reworking old posts. We only scan `Posted/` to see what has already been done, what worked, and to avoid repeating ourselves.

---

## Post versioning

**RULE: One post = one file. No duplicates.**

- When reworking/rewriting a post → overwrite the CURRENT file, DO NOT create `-v2`, `-v3`
- Exception: only if the user has EXPLICITLY asked to preserve the old version
- If you need a change history → write it in `notes:` in the frontmatter (date + what changed)
- Old duplicates (`-v2`, `-v3`) → delete, keep a single file

---

## What NOT to do

- Don't invent stories that aren't in the DIP Stories Bank
- Don't add "filler" — the author's expertise is the foundation
- Don't "polish" until the author's voice is gone
- Don't use generic phrases like "In today's world...", "Let me share...", "Excited to announce..."
- Hashtags: **1–3 max** (360Brew understands context from the text directly; >3 = spam risk). Relevant keywords inside the text itself matter more than hashtags
- Don't add links in the post body (**~60% reach penalty**). "Link in first comment" is also penalized (2026). If a link is necessary — full value in the post first, link after ~300 characters
- Don't use published posts as source material for new posts (see "canonical vs derivative" above)
