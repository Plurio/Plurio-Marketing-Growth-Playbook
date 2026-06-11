# Lovable Carousel Instructions — LinkedIn

> Instructions for creating LinkedIn carousels in Lovable.
> Used as a prompt (whole or by section) when generating slides.
> **Last updated:** 2026-03-23

---

## General prompt template for Lovable

```
Create a LinkedIn carousel with [N] slides.
Size: 1080x1350px (vertical 4:5).
Export as PDF.

Visual mode: [BUILDER / PRODUCT]
[See mode-specific instructions below]

Slide content:
[Paste slide text here]
```

---

## Mode: BUILDER (dark)

### Lovable prompt

```
Create a LinkedIn carousel PDF. Vertical 4:5 (1080x1350px). [N] slides.

DESIGN:
- Background: #0D0D0D (near-black), solid, no gradients
- Main text: #FFFFFF (white)
- Headers: bold, monospace font (Source Code Pro, JetBrains Mono, or Roboto Mono)
- Body text: clean sans-serif (Inter or system default), regular weight
- Accent color: #C8D830 (lime-yellow) — use for: step labels, arrow markers (→), key numbers, CTA text, highlighted phrases
- Secondary text: #9CA3AF (grey) — use for: subtitles, small text, "It's not. This is where it gets interesting."
- Slide numbering: bottom-left corner, small, grey, format "1/9"

LAYOUT:
- Text aligned LEFT (not centered), except transition slides
- Generous whitespace — don't fill empty space with decoration
- No icons, no illustrations, no stock graphics
- Each slide scannable in 3-5 seconds
- Step label: monospace, uppercase, small, accent color (e.g., "STEP 1")
- Header: monospace, bold, large (e.g., "Solve It Together")
- Body: sans-serif, regular, medium size
- Arrow markers "→" in accent color for lists

SPECIAL SLIDES:
- Slide 1 (COVER): Large bold monospace text, takes up ~40% of slide. Small text at bottom in grey. No logo.
- Transition slides: Text centered vertically, larger font, more whitespace. Creates a "pause" in the narrative.
- Last slide: Author name + company at bottom, small monospace grey text. Format: "Author Name · Company"

DOCUMENT TITLE: [title for the carousel — shown when uploaded to LinkedIn]

NO:
- No Plurio logo (except text mention on last slide)
- No decorative elements
- No gradients or shadows
- No rounded corners on text blocks (unless it's a list item background)
- No emojis
```

### Example: list items with backgrounds (as in Slide 4 of the current carousel)

```
For list items with "→" markers:
- Each item on a subtle dark-grey background (#1A1A1A or #1C1C1C)
- Monospace font, accent color for the "→" and text
- Slight padding, no rounded corners (or very subtle 4px radius)
- Stack vertically with small gap between items
```

---

## Mode: PRODUCT (branded)

### Lovable prompt

```
Create a LinkedIn carousel PDF. Vertical 4:5 (1080x1350px). [N] slides.

DESIGN:
- Background: #FFFFFF (white)
- Main text: #1A1A1A (near-black)
- Headers: Inter Display Bold or Manrope Bold, large
- Body text: Inter Regular, medium
- Accent color: #F5DC4A (Plurio Yellow) — use for: highlights, metric callouts, key phrases background
- Secondary accent: #0D0D0D (black) for high-contrast elements
- Borders/dividers: #E5E7EB (light grey)
- Slide numbering: bottom-left corner, small, grey

LAYOUT:
- Clean, professional SaaS aesthetic
- Text aligned LEFT
- Generous whitespace
- Cards/sections can have light grey (#F3F4F6) background
- Metrics/numbers: large bold + yellow highlight background

LOGO:
- Slide 1: Plurio logo (icon + "plurio" text) — top-left or bottom, small
- Last slide: Plurio logo + author name
- Logo file reference: Plurio icon (intersecting ovals on yellow rounded square) + "plurio" in custom font

SPECIAL SLIDES:
- Slide 1 (COVER): Large headline, clean, professional. Logo small.
- Data slides: Numbers large and prominent, context smaller
- Last slide: CTA + logo + author

NO:
- No dark backgrounds
- No monospace fonts
- No terminal/developer aesthetic
- No decorative stock images
```

---

## Document Title (carousel caption in LinkedIn)

When a PDF is uploaded to LinkedIn, the document has a **title/name** — visible in the interface as the caption under the carousel. This is an important element — essentially a second hook.

### Rules for the Document Title

1. **Short:** 5–8 words maximum
2. **Informative:** what the reader will get from swiping through
3. **Doesn't duplicate the hook** of the post — complements it
4. **Format:** Title Case or Sentence case, no emoji
5. **Includes a keyword** for search (LinkedIn indexes document titles)

### Formula

```
[What it is] + [For whom / About what]
```

### Examples

| Post | Document Title |
|------|---------------|
| Agents Building Agents (7 steps) | `From Manual Workflow to Autonomous Agent: 7 Steps` |
| Verification chain (Kirill) | `5-Step Agent Verification Chain` |
| Creative fatigue detection | `When to Kill a Creative: Decision Framework` |
| Product feature carousel | `Plurio AI: How Workflow Automation Works` |

### Anti-patterns

- "Carousel" or "Slides" in the title — obvious, not needed
- Too generic: "AI Agents Guide" — says nothing
- Clickbait: "You Won't Believe..." — not our style
- Too long: gets cut off in the mobile feed

---

## Checklist before sending to Lovable

- [ ] Visual Mode determined (BUILDER / PRODUCT / MEME / PERSONAL)
- [ ] All slide text finalized and checked against the original
- [ ] Number of slides: 6–9 (optimum)
- [ ] First slide is a strong visual hook (readable as a thumbnail)
- [ ] There is a transition slide (if 7+ slides) — for rhythm
- [ ] Last slide: CTA + author attribution
- [ ] Logo: per the mode's rules (BUILDER = text, PRODUCT = icon)
- [ ] Document Title prepared
- [ ] Size: 1080x1350px (4:5 vertical)
- [ ] Format: PDF export

---

## Workflow: post with a carousel (from text to publishing)

```
1. Post text is ready (Post-Creation-Engine)
        ↓
2. Claude recommends a Visual Mode
   (per the Decision Matrix in Visual-Design-System.md)
        ↓
3. Claude prepares:
   - Slide text (content split by slides)
   - Document Title
   - Lovable prompt (per the template above)
        ↓
4. The user sends it to Lovable
        ↓
5. Gets the PDF → uploads to LinkedIn
        ↓
6. In the post file (Posted/Author/YYYY-MM-DD-slug.md):
   - "Carousel Slides" section — slide text
   - "Notes for Lovable" section — design notes
   - Document Title in metadata
```
