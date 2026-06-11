# Visual Design System — LinkedIn Content

> Visual system for LinkedIn content. Defines styles, palettes, and rules for each post type.
> Used when recommending visuals and generating instructions for Lovable.
> **Last updated:** 2026-03-23

---

## Brand Reference — Plurio

### Logo

- **File:** `Content/Working-Materials/Plurio_logotype 1-1 (1).png`
- **Elements:** Icon (intersecting ovals on a yellow rounded square) + "plurio" text + "by Elly Analytics" subtitle
- **Usage variants:** icon alone, full logo, text without icon

### Brand Colors (extracted from logo + plurio.ai website)

| Name | Hex | Where used |
|----------|-----|-----------------|
| Plurio Yellow | `#F5DC4A` | Primary brand color, logo icon background |
| Black | `#000000` / `#1A1A1A` | Text, logo icon |
| White | `#FFFFFF` | Website background, light slides |
| Light Grey | `#9CA3AF` | Subtitles ("by Elly Analytics"), secondary text |
| Near-Black (dark mode) | `#0D0D0D` / `#111111` | Dark background for builder content |

### Typography (plurio.ai website)

| Level | Font | Use |
|---------|-------|---------------|
| Primary | Inter / Inter Display | Headlines, body — clean, modern |
| Monospace | Roboto Mono / JetBrains Mono | Code-style content, builder aesthetic |
| Secondary | IBM Plex Sans, Manrope | Alternatives for variety |

### Speaker photos


---

## Visual Modes — 4 modes

Each content type is tied to a visual mode. The mode defines palette, typography, mood, and logo rules.

### Mode 1: BUILDER (dark)

**When:** Framework carousels, how-to processes, step-by-step, numbered lists, technical breakdowns, "build in public"

**Palette:**
- Background: `#0D0D0D` (near-black)
- Primary text: `#FFFFFF` (white)
- Headings: `#FFFFFF` bold
- Accent: `#C8D830` (lime-yellow, like in the current carousel) — for highlighting key numbers, CTAs, "→" markers
- Secondary text: `#9CA3AF` (grey)

**Typography:**
- Headings: Monospace bold (Roboto Mono / JetBrains Mono / Source Code Pro)
- Body: Sans-serif (Inter / system)
- Accents/lists: Monospace

**Logo:** Only on the last slide, "Seva Ustinov · Plurio" or "Kirill Kasimskiy · Plurio" as text (monospace, small). NO icon logo — too "corporate" for builder content.

**Mood:** Terminal, code editor, "showing how I build". Minimalism. Lots of whitespace. Text left-aligned.

**Example posts:** Agents Building Agents (7 steps), any framework carousels, technical playbooks

---

### Mode 2: PRODUCT (branded)

**When:** Product announcements, Plurio features, demo screenshots, product case studies, launch posts

**Palette:**
- Background: `#FFFFFF` (white) or `#F9FAFB` (off-white)
- Primary text: `#1A1A1A` (near-black)
- Accent: `#F5DC4A` (Plurio Yellow) — for highlights, buttons, icons
- Secondary accent: `#0D0D0D` (black) for contrast
- Borders/dividers: `#E5E7EB` (light grey)

**Typography:**
- Headings: Inter Display Bold / Manrope Bold
- Body: Inter Regular
- Numbers/metrics: Inter Bold + Plurio Yellow background

**Logo:** Full logo (icon + "plurio") on the first AND last slide. This is product content — branding is appropriate.

**Mood:** Clean SaaS, professional, "we are a serious company with a serious product". But not overdesigned — content > ornament.

**Example posts:** Product launches, feature announcements, agent demo screenshots, customer case studies

---

### Mode 3: MEME / CULTURE (loose)

**When:** Memes, humor posts, cultural references, relatable content, hot takes with an image

**Palette:** Defined by the meme/image itself. Post text — text-only (no slides). The image = native image attachment.

**Typography:** Not applicable (the meme sets its own style).

**Logo:** NEVER. Meme + logo = corporate cringe.

**Mood:** Authentic, "found something funny and sharing it". Don't try to stylize the meme to fit the brand.

**Rules:**
- Upload the meme as-is — don't crop, don't add frames
- Post text short and punchy (800–1,200 characters)
- Single image format usually -30%, but memes are an exception (humor + relatability = shares)

**Example posts:** Dashboards iceberg meme (Kirill), any future meme posts

---

### Mode 4: PERSONAL / STORY (photo)

**When:** Personal stories, community events, "behind the scenes", team photos, event recaps

**Palette:** The photo sets the palette. Don't add overlays, filters, or text on top of the photo.

**Typography:** Not applied to the visual. Only the post text.

**Logo:** NEVER on the photo. You can mention "Plurio" or "Elly Analytics" in the text, but the visual is purely personal.

**Mood:** Authentic, real, "this is me and my life". Photo without filters (or minimal correction).

**Rules:**
- Photo is uploaded as a native image
- If multiple photos — multi-image (up to 5), not a carousel
- If photo + long text — photo first, the text provides context

**Example posts:** Vibe Salon (event photo), team events, conference photos

---

## Decision Matrix — which mode to pick

| Content type | Visual Mode | Format | Logo |
|-------------|-------------|--------|------|
| Framework / How-to / Process | **BUILDER** (dark) | Carousel (PDF) | Last slide only, as text |
| Numbered steps / Playbook | **BUILDER** (dark) | Carousel (PDF) | Last slide only, as text |
| Product feature / Launch | **PRODUCT** (branded) | Carousel or Multi-Image | First + last slide |
| Case study with product | **PRODUCT** (branded) | Carousel | First + last slide |
| Meme / Humor | **MEME** (loose) | Text + Image | Never |
| Personal story / Event | **PERSONAL** (photo) | Text + Photo | Never |
| Podcast announcement | No visual | Text Only | N/A |
| Hot take / Opinion | No visual | Text Only | N/A |
| Before/After comparison | **PRODUCT** | Multi-Image | Optional on the first |
| Data / Charts / Metrics | **BUILDER** or **PRODUCT** | Carousel | Case by case |

---

## Logo Rules (summary)

| Situation | Logo | How |
|----------|------|-----|
| Builder carousel (personal post) | "Author · Plurio" text | Last slide, monospace, small, at the bottom |
| Product carousel | Full logo (icon + text) | First + last slide |
| Meme | None | — |
| Photo | None | — |
| Text-only post | N/A | — |
| Plurio AI corporate page | Full logo | Every visual |

**Principle:** Seva's/Kirill's personal posts are PERSONAL posts. The Plurio logo = mention, not branding. For product content the logo is appropriate, because it is about the product.

---

## Slide Design Rules (all modes)

### Mandatory principles

1. **Scannable in 3–5 seconds.** Each slide — one thought. If it can't be read in 5 seconds — too much text.
2. **First slide = thumbnail.** Bold, large text, readable in a small size in the feed. This is the visual "hook".
3. **Whitespace > ornament.** Whitespace is a tool. Don't fill the void with decoration.
4. **Text left-aligned.** Centered — only for transition slides (pause/emphasis).
5. **Slide numbering** — optional, small in the corner (1/9, 2/9...). Helps with orientation.
6. **Size:** 1080x1350px (vertical 4:5) — optimal for the LinkedIn mobile feed.
7. **File format:** PDF upload.

### Text hierarchy on a slide

| Element | Style | Example |
|---------|-------|--------|
| Step label | Monospace uppercase, small, accent color | `STEP 1` |
| Heading | Bold, large, primary color | **Solve It Together** |
| Body text | Regular, medium, primary color | Ask an agent to solve a real task. |
| Accent text | Monospace bold, accent color | `"continue" from time to time.` |
| List markers | Arrow `→`, accent color | `→ A reusable template` |
| Footer | Monospace, small, secondary color | `Seva Ustinov · Plurio` |

---

## Per-Author Visual Preferences

| Author | Preferred Mode | Rationale |
|-------|---------------|-------------|
| Seva | BUILDER | Builder-in-chief, technical content, "shows how it's made" |
| Kirill | BUILDER or PRODUCT | Client-facing, data-driven. Builder for frameworks, Product for case studies |
| Ella | PRODUCT or PERSONAL | Workflow guides, team processes |
| Denis | BUILDER | CPO frameworks, decision systems |
| Plurio AI (company page) | PRODUCT | Always branded |

---

## Website Reference

**URL:** https://plurio.ai

When creating PRODUCT-mode visuals — reference the site's style:
- Clean white background
- Inter typography
- Minimalism
- Plurio Yellow as accent (not dominant color)
- Black text, grey captions

The site screenshot is NOT stored here — always reference the current version at the URL.

---

## System evolution

The system evolves after every 3–4 carousels:
1. Gather performance data (impressions, saves, engagement)
2. Compare BUILDER vs PRODUCT modes
3. A/B test: the same framework — in dark and in light
4. Update recommendations

**Current status:** v0.1, first carousel (Agents Building Agents, BUILDER mode). Performance data needed for validation.
