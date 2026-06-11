# Visual Brief Engine

> Skill for generating visuals for a LinkedIn post. Input — a finished post draft + the author's DIP + Visual-Design-System. Output — a visual concept + concrete prompts for Higgsfield (images/video) and HeyGen (talking heads/avatars).
>
> **Status:** v0.1 — experimental phase. The first 5–10 cases are captured in `Visual-Style-Experiments.md`, then patterns are generalized into the DIP and this skill.

---

## When to use

Triggers:
- A finished post in `Posted/[Author]/` needs a visual (hero image for native attachment, short clip, Soul Character avatar).
- The user asks: "Generate a visual for the post", "Pick an image for X", "Need a video clip for the post about Y".
- After `/create-post` — runs automatically as Step 9 (Visual Brief).

DO NOT use:
- When you need a carousel slide → use `Visual-Design-System.md` directly (Lovable / Figma → PDF).
- When you need a real photo from an event → PERSONAL mode, no generation.
- When the post is text-only (podcast announcement, hot take) → no visual needed.

---

## Inputs (mandatory read before brief)

1. **Finished post draft** in `Posted/[Author]/YYYY-MM-DD-[slug].md`
2. **Author's DIP** — `01-Digital-Identity-Profiles/[Author]-DIP.md` (for tone, cluster, visual preferences)
3. **Visual-Design-System.md** — for palette, modes, per-author preferences
4. **Visual-Style-Experiments.md** — log of past experiments (what worked, what didn't)

---

## Pipeline (8 steps)

### Step 1: Determine the visual need

Read the post and answer 4 questions:

| Question | Possible answers |
|--------|------------------|
| Which cluster? | AI-Native Teams / Performance Marketing / Founder Journey / Industry Insights / Events |
| Which mode per Visual-Design-System? | BUILDER / PRODUCT / MEME / PERSONAL / Hero-Photo (new) |
| What is needed? | Hero image (1) / Short video clip (1) / Soul Character avatar / Talking-head (HeyGen) / Asset reuse from HeyGen library |
| Aspect ratio? | 1:1 (square, default LinkedIn), 4:5 (vertical, for mobile), 16:9 (horizontal, for headers) |

### Step 2: Extract the "visual anchor" from the post

Find in the post ONE concrete scene / metaphor / physical object that can be shown.

**Good anchors:**
- A specific place/setting ("late night office", "marketing team meeting room")
- A physical process ("hands typing", "dashboard on screen")
- A metaphor ("trust line — where a person lets go of the wheel")
- A specific moment from a story ("Black Friday war room")

**Bad anchors (do NOT visualize):**
- Abstract claims ("trust matters")
- Generic "AI agent" icons (look generic)
- Stock "people in an office pointing at a laptop"

### Step 3: Pick a model

| Task | Higgsfield model | HeyGen |
|--------|-------------------|--------|
| Photorealistic hero image | Soul / Soul 2.0 | — |
| Stylized illustration | Flux 2 / Nano Banana Pro | — |
| Cinematic still | Cinema Studio (Soul) | — |
| Short B-roll video (5–10s) | Seedance 2.0 / Kling 3.0 | — |
| UGC-style video | UGC Factory (Higgsfield) | — |
| Talking-head with avatar | — | Avatar + script |
| Multilingual video version | — | Lipsync in 175+ languages |
| Reuse of an existing cut clip | — | Library lookup |

### Step 4: Write the Higgsfield prompt

**Prompt structure:**
```
[Subject] in [setting], [action], [mood/lighting], [camera angle], [style].
Aspect ratio: [1:1 / 4:5 / 16:9]
Model: [Soul / Flux 2 / Cinema Studio / Seedance 2.0]
```

**Applying a Visual-Design-System mode:**

- **BUILDER mode** → dark scene, monospace aesthetic, terminal/code-editor backdrop, minimal, lime-yellow accents
- **PRODUCT mode** → clean white/off-white backdrop, professional SaaS look, Plurio Yellow accent
- **PERSONAL/Hero-Photo** → cinematic editorial photography, natural light, real environments

**Example (BUILDER mode, hero image):**
```
A solo marketer at a dark desk late at night, two monitors showing
performance dashboards, focused expression, side light only, shot on
35mm film aesthetic, shallow depth of field, terminal-green accents
on screens.
Aspect ratio: 1:1
Model: Soul 2.0
```

### Step 5: Write the HeyGen prompt (if a talking head is needed)

**When to use HeyGen:**
- Seva/Kirill/Denis/Ella delivers a key thought on camera (3–15 seconds)
- Multilingual adaptation of an existing post
- Reuse of cut footage from the library

**HeyGen task structure:**
```
Avatar: [Seva / Kirill / Denis / Ella / Custom]
Voice: [Native EN / RU / ...]
Script (verbatim, ≤30 sec):
[One or two key claims from the post rewritten for spoken delivery]
Background: [office / studio / minimal]
Output: 1080x1080 / 1080x1350 / 1920x1080
```

**Reuse mode:**
First, via MCP request:
```
heygen_list_assets(folder="webinar-clips-2026-03-18", duration_max=15)
```
If a suitable clip is found — DO NOT generate a new one, reuse it with proper cropping and subtitling.

### Step 6: Generate

**If MCPs are connected:**
- Higgsfield → MCP call with the prompt → poll → get the asset URL
- HeyGen → MCP call or library lookup

**If MCPs are not connected:**
- Return the prompt as text — the user copies it into the Higgsfield/HeyGen UI and generates manually

### Step 7: Save in the post metadata

Add to the post frontmatter:
```yaml
visuals:
  hero_image:
    url: [Higgsfield URL after generation]
    prompt: [full prompt]
    model: [Soul 2.0]
    aspect_ratio: 1:1
    generated_at: 2026-05-07
  video:
    url: [HeyGen URL or Higgsfield URL]
    type: [native_attachment / first_comment / reuse]
    duration_sec: 8
    script: [if HeyGen — verbatim script]
attached_to_post: native  # native attachment to post, NOT in first comment
```

### Step 8: Log in the Experiments journal

Add a new row to `Visual-Style-Experiments.md`:
- Date | Post | Mode | Anchor | Prompt | Asset | Reaction (to be filled after publishing)

---

## Per-Cluster Defaults

Default settings for each cluster (overridable):

| Cluster | Default Mode | Default Model | Default Format |
|---------|--------------|---------------|----------------|
| AI-Native Teams & AI-Marketing | BUILDER | Soul 2.0 (cinematic) | Hero image 1:1 |
| Performance Marketing + Product | BUILDER or PRODUCT | Cinema Studio / Flux 2 | Hero image 1:1 + optional 8-sec Seedance video |
| Founder Journey & Leadership | PERSONAL/Hero-Photo | Soul 2.0 | Hero image 1:1, real-environment |
| Industry Insights & Contrarian Takes | BUILDER or MEME | Flux 2 / Nano Banana Pro | Single image 1:1 |
| Events / Thought Leadership | PRODUCT | Soul 2.0 + HeyGen library lookup | Hero image + reused webinar clip |

---

## Anti-patterns

Below is what NOT to generate. These patterns perform poorly on LinkedIn.

- Generic "AI/robot" stock art — looks cheap, reads as stock
- Smiling people in offices pointing at laptops — last century
- 3D render with floating UI elements — visual noise, untethered to meaning
- Text overlay on top of AI generations — better to use native LinkedIn caption
- Over-stylized illustrations as "tech-illustration" — loses authenticity
- Soul Character with unnatural facial expressions — better to regenerate or use a real photo
- Videos longer than 15 seconds for LinkedIn — sharp drop-off after 8–10 sec

---

## Visual Brief Template

For each post, fill in:

```markdown
## Visual Brief — [Post Slug]

**Cluster:** [AI-Native Teams / ...]
**Mode:** [BUILDER / PRODUCT / ...]
**Need:** [Hero image / Video / Both / Reuse]
**Aspect Ratio:** [1:1 / 4:5 / 16:9]

### Anchor
[Specific scene/metaphor/object from the post]

### Higgsfield Prompt
```
[Full prompt]
```
**Model:** [Soul 2.0 / Flux 2 / ...]
**Aspect:** [1:1]
**Variations to generate:** [3-5]

### HeyGen Brief (if needed)
**Avatar:** [Seva / ...]
**Script (≤30s):**
```
[Verbatim script]
```
**Voice:** [EN native]
**Reuse check:** [Library folder to search before generating new]

### Expected output
- Hero image: 1080x1080 PNG
- Optional video: 8s MP4

### Notes
[Anything special — colors to avoid, brand alignment, etc.]
```

---

## MCP Commands Reference

Once MCPs are connected — via Claude in Cowork:

**Higgsfield:**
- `higgsfield_generate_image(prompt, model, aspect_ratio)` — generate single image
- `higgsfield_generate_video(prompt, model, duration_sec)` — generate video
- `higgsfield_list_history()` — browse past generations
- `higgsfield_train_character(reference_images[])` — Soul Character training

**HeyGen:**
- `heygen_list_assets(folder, duration_max)` — browse library
- `heygen_create_video(avatar, script, voice)` — generate talking head
- `heygen_translate_video(asset_id, target_language)` — multilingual adaptation

(Exact tool names to be checked after connecting via `tools_list`.)

---

## Evolution

After every 5 cases in `Visual-Style-Experiments.md`:
1. What worked (engagement, reactions in chat) → pattern goes into the author's DIP
2. What didn't work → anti-pattern goes into this file
3. Which mode most often works → update per-cluster defaults

**Goal v1.0:** After 10–15 cases, lock in a stable visual language for each author and minimize "taste-based" decisions.
