# Voice Input Workflow — Voice → LinkedIn Post

> Pipeline for processing voice input and turning it into an optimized post.

---

## Input scenarios

| Scenario | Input | What to do |
|----------|------|-----------|
| **Direct voice into the agent** | A person dictates thoughts via Wisp Pro Flow or sends a voice message straight to Claude | Text is already transcribed → go straight to processing |
| **Voice note (file)** | .m4a, .ogg, .mp3, .wav file | Transcribe via Whisper → then process |
| **YouTube/video recording** | URL or local video file | Transcribe via `transcribe-video.py` → then process |
| **Meeting recording (Granola)** | Meeting is already in Granola | Export via your meeting-transcript export tool → extract the author's speech → process |
| **Meeting recording (Fireflies)** | Meeting recorded in Fireflies | Sync via Fireflies tool → extract the author's speech → process |
| **Text notes** | Telegram post, notes, workflow description | Go straight to processing |

---

## Step 1: Get the transcript

### If voice is already transcribed (Wisp Pro Flow, text)
→ Skip this step, go to Step 2.

### If it's an audio/video file

**Local file (.m4a, .mp3, .wav, .mp4, .mov):**
```bash
cd Scripts/Integrations/AudioTranscription
.venv/bin/python transcribe-video.py --file [path] --lang [ru|en] --model medium
```

**YouTube URL:**
```bash
cd Scripts/Integrations/AudioTranscription
.venv/bin/python transcribe-video.py --url "[URL]" --lang [ru|en] --model medium
```

**Granola:**
```bash
```

### Result
A markdown file with transcribed text, ready for processing.

---

## Step 2: Extract content from the input

Read the transcript/text and extract:

### 2.1 Key ideas
- What are the main thoughts the author voiced?
- Are there specific numbers, facts, examples?
- Are there personal stories or cases?
- Is there an opinion/stance (especially a contrarian one)?

### 2.2 Volume assessment
- One idea → one post
- 2–3 ideas → propose a series of posts or pick the strongest one
- A large content block → break it into a series with a shared thread

### 2.3 What NOT to include
- Internal details, NDA, confidential information
- Client names without permission
- Unfinished thoughts without context
- "Filler" and repetitions (natural in voice input)

---

## Step 3: Run the Post Creation Engine

Pass the extracted content to **Post-Creation-Engine.md** (Steps 1–7).

In doing so:
1. Identify the author
2. Load their DIP
3. Find the best angle
4. Pick a format
5. Write the post in the author's voice
6. Validate
7. Return the output

---

## Step 4: Feedback

After delivering the draft:
- If the author says "redo it" / "wrong tone" → return to Post Creation Engine Step 4, adjust
- If the author says "add this" → integrate the new content
- If the author says "split into a series" → create 2–3 connected posts with a shared thread
- If the author approves → save to `Posted/[Author]/YYYY-MM-DD-[slug].md`

---

## Step 5: Update the DIP (if needed)

If the voice input contained:
- New stories not captured in the DIP → record them in the DIP Stories Bank
- New expertise topics → update DIP Expertise Clusters
- New speech patterns → record in DIP Tone of Voice

Follow `_DIP-Update-Workflow.md`.

---

## Quick flow (for everyday use)

```
Author dictates thoughts
        │
        ▼
Claude extracts key ideas
        │
        ▼
Claude loads the author's DIP
        │
        ▼
Claude applies Algorithm + Trends
        │
        ▼
Claude creates the post + 2-3 hooks + format recommendation
        │
        ▼
Author reviews → feedback → final version
        │
        ▼
Save to Posted/[Author]/
```

Typical time: 5–10 minutes from voice input to a ready-to-publish post.
