---
name: nt-brand-guidelines
description: Applies NT (National Telecom) official brand colors, typography, and layout standards to PowerPoint presentations. Use this skill whenever creating or styling slides for NT, including any mention of "NT template", "NT slides", "NT presentation", "NT style", "NT brand", "NT deck", or when the user asks to create presentation slides in the NT corporate format. Also trigger when editing an existing NT-branded presentation, or when a logo/icon/font for NT is needed. This skill ensures correct use of NT yellow (#FFD100, PANTONE 109C), the recommended secondary palette (teal, dark grey, brick red, brown), the real bundled NT Bold/NT Regular font files, the four official logo lockups, the "Vital Sign" icon family, LAYOUT_WIDE dimensions, proper logo placement, and the signature rounded pill-shape visual motif.
---

# NT (National Telecom) Brand Styling for Presentations

## Overview

This skill provides NT's official brand identity specifications for creating PowerPoint slide decks. It bundles the official NT presentation template and defines all visual rules: colors, fonts, slide dimensions, logo usage, layout patterns, and prohibited elements.

**Keywords**: NT, National Telecom, NT template, NT slides, NT brand, NT presentation, corporate identity, Thai telecom, brand colors, slide styling, NT Bold, NT Regular, yellow branding

## Quick Start

Resolve bundled files relative to this skill directory. When scripting, set `NT_SKILL_DIR` to the absolute path of this folder and build asset paths from that value.

There are two ways to create NT-branded presentations:

1. **Template-based editing** (recommended for speed): Use the bundled template at `assets/NT_Presentation_Template.pptx` as the source deck. In Codex, use the `Presentations` skill/template-following workflow: inspect the master/layout hierarchy, duplicate or reuse selected layouts, fill placeholders locally, and render every final slide for visual QA.

2. **Create from scratch** (for full control): Use Codex presentation tooling, preferably `@oai/artifact-tool` from the `Presentations` skill when available, with the brand specifications below. If working outside that workflow, translate these constants and layout rules to the local PPTX library.

For detailed layout-by-layout specifications, read `references/layouts.md`.

---

## Brand Colors

Source: official NT brand manual color specification (corrected from earlier approximation).

### Primary: NT Yellow

The signature color, representing creativity and innovation.

| Spec | Value |
|------|-------|
| PANTONE | 109 C |
| RGB | 255, 209, 0 |
| CMYK | 0, 17, 100, 0 |
| **HEX** | **`#FFD100`** |

**Usage principle:**
- NT Yellow should be the dominant component in any NT-branded design — give it a clearly prominent role, generally **more than 60% of the visual proportion** of the piece (title slides, section dividers, closing slides, hero/banner elements).
- Opacity can be adjusted for depth/layering, but must **never go below 10%** — even at its lightest, the yellow should remain perceptible rather than disappear.
- On dense, data-heavy slides (tables, charts, long body text) a full 60%+ yellow fill will hurt readability — in that case, keep NT Yellow prominent in the *frame* (header band, sidebar, title bar, section markers) rather than the content background itself, so the brand presence stays strong without competing with the data.

### Recommended Secondary Palette

Used alongside NT Yellow for storytelling and to add variety while staying in the NT tone — not standalone brand colors, always paired with yellow as the anchor.

| Role | PANTONE | HEX | CMYK |
|------|---------|-----|------|
| **Teal** | 7465 C | `#40C1AC` | 65, 0, 38, 0 |
| **Dark Grey** | 425 C | `#545859` | 63, 41, 45, 33 |
| **Brick Red** | 7625 C | `#E1523E` | 0, 80, 78, 0 |
| **Brown** | 7587 C | `#924C2E` | 6, 70, 83, 38 |

### White / Black

| Role | Hex | Usage |
|------|-----|-------|
| **White** | `#FFFFFF` | Content slide backgrounds, text on dark-accent backgrounds (never on NT Yellow — see contrast note below) |
| **Black** | `#000000` | Primary text on white backgrounds |
| **Near-Black** | `#212121` | Alternative dark text (slightly softer) |
| **Mid Gray** | `#888888` | Muted labels, footnotes |

**Text on secondary-color fills** (checked by WCAG contrast ratio, not assumed): Teal `#40C1AC` and Brick Red `#E1523E` are light enough that they need **black** text (white on teal is 2.2:1 — fails even large-text minimum). Brown `#924C2E` and Dark Grey `#545859` are dark enough that they need **white** text (black on dark grey is 2.9:1 — fails). Don't default to "white on any dark-looking color" — verify per color.

### Gradients

The brand manual shows gradients for NT Yellow and each secondary color, running from **white (or a very light tint) up to the full 100% color**. Use these gradients on decorative fills and background shapes to add visual variety while keeping everything recognizably on-brand — never introduce a gradient toward a hue outside the approved palette.

**Exception — graphic elements**: signature graphic elements (e.g. the "Next Vital Sign" motif) must use the **full 100% color only** — no gradient, no reduced opacity — to preserve their visual prominence.

### Color Rules

- **Text on white backgrounds**: Use `#000000` or `#212121`
- **Text on yellow backgrounds**: Always use `#000000` — NT Yellow (`#FFD100`) is too light for white text to read against (contrast ratio ~1.5:1, fails WCAG even for large text)
- **Accent shapes / primary brand fills**: `#FFD100` (NT Yellow), proportion >60% where the layout allows it
- **NEVER use black backgrounds** — this is a strict NT brand prohibition
- **NEVER use dark/black background slides** — all slides must be white or yellow backgrounds only
- **Never use yellow at less than 10% opacity** — it must stay visible even in its lightest tint
- Charts and data visualizations: anchor on `#FFD100` (NT Yellow) and draw supporting series from the recommended secondary palette — `#40C1AC` (teal), `#545859` (dark grey), `#E1523E` (brick red), `#924C2E` (brown) — five colors total, which is enough for most category counts without needing to invent additional hues

> **Template asset status**: `assets/NT_Presentation_Template.pptx` has been regenerated with the corrected `#FFD100` throughout (all layouts, master, and presentation defaults), so the template and this spec are now consistent.

---

## Typography

### Font Files (bundled, real assets)

The actual NT typeface files are bundled at:
- `assets/fonts/NT_Bold.ttf` — internal font name `NT`, style `Bold`
- `assets/fonts/NT_Regular.ttf` — internal font name `NT`, style `Regular`

**To make these render correctly (not fall back) when generating or QA-rendering a .pptx in a Codex environment**, install them into the local font cache before creating slides or running visual QA:

```bash
mkdir -p ~/.fonts
cp "$NT_SKILL_DIR"/assets/fonts/*.ttf ~/.fonts/
fc-cache -f
```

After this, reference the font by its real family name `NT` (with `Bold`/`Regular` as the style) in presentation code — not "NT Bold" as a single font-face string — so LibreOffice's QA render and PowerPoint both resolve to the correct weight:

```javascript
// Use the family name and set bold separately.
slide.addText("Heading", { fontFace: "NT", bold: true });   // resolves to NT Bold
slide.addText("Body copy", { fontFace: "NT", bold: false }); // resolves to NT Regular
```

If the font isn't installed in the Codex environment (e.g. a fresh session where the install step was skipped), LibreOffice will substitute a fallback for QA preview purposes only — the fallback chain below still applies for that case, and for recipients opening the file on a machine without the NT font installed.

### Font Families

| Role | Font | Fallback |
|------|------|----------|
| **Headings / Titles** | NT Bold | Helvetica Neue Medium → Arial Black → Arial |
| **Body Text** | NT Regular | Helvetica Neue Medium → Calibri → Arial |
| **Secondary** | Helvetica Neue Medium | Calibri |

### Size Guidelines

| Element | Size | Weight |
|---------|------|--------|
| Slide title | 28–36pt | NT Bold |
| Section header / subtitle | 20–24pt | NT Bold |
| Body text | 14–16pt | NT Regular |
| Captions / footnotes | 10–12pt | NT Regular, color `#888888` |
| Large stat callouts | 48–72pt | NT Bold |
| Copyright footer | 8–10pt | NT Regular, color `#000000` |

### Font Application in JavaScript Presentation Code

```javascript
// The bundled files register the family as "NT"; choose weight separately.
const FONT_NT = "NT";
const FONT_FALLBACK_HEADING = "Arial";
const FONT_FALLBACK_BODY = "Calibri";

// Example text options:
const headingTextOptions = { fontFace: FONT_NT, bold: true };
const bodyTextOptions = { fontFace: FONT_NT, bold: false };
```

---

## Slide Dimensions

Always use **LAYOUT_WIDE**: **13.333" × 7.5"** (widescreen)

In Codex's `Presentations` workflow, use a wide 16:9 PowerPoint canvas matching 13.333" x 7.5". If using a library that exposes PowerPoint layout constants, choose `LAYOUT_WIDE`.

---

## Logo Usage

### Official Logo Lockups (bundled, real assets)

Four official lockups are bundled at `assets/logos/`. All four use the same icon mark (`#FFD100` yellow bars) + `#545859` dark grey wordmark, on a transparent/white background — verified by direct pixel sampling of the files.

| File | Size (px) | Contents | Use When |
|------|-----------|----------|----------|
| `NT_1_v3.png` | 746×497 | Icon + "nt" only, no company name | Small spaces — favicons, compact headers, watermarks, anywhere the full name would be illegible at size |
| `NT_2_v3.png` | 1225×551 | Icon + "nt" + English "National Telecom" (2-line) | English-language materials, international audiences |
| `NT_3_v3.png` | 1230×514 | Icon + "nt" + Thai "โทรคมนาคมแห่งชาติ" (2-line) | Thai-language materials, internal NT communications |
| `NT_4_v3.png` | 2755×529 | Icon + "nt" + Thai + English (full, wide lockup) | Formal/legal documents, cover pages, closing slides, anywhere the full legal name should appear |

### Known gap — no dedicated yellow/dark-background variant

All four lockups have a **yellow icon** (`#FFD100`). On a yellow (`#FFD100`) background, the icon bars will disappear into the background — only the dark grey wordmark stays visible. None of the bundled files is a reversed/white or monochrome variant designed for yellow or dark backgrounds.

Until a proper reversed variant is provided:
- **Prefer white backgrounds for the logo** wherever the layout allows it.
- If the logo must sit on a yellow background, use `NT_1_v3.png` (icon+wordmark only, most compact) — its dark grey "nt" text still reads clearly, only the icon bars are essentially invisible.
- Flag to the user if a section divider or closing slide needs the logo on yellow and legibility of the icon specifically matters — a reversed/white version should be requested rather than approximated.

### Placement Rules

- **Logo position**: Bottom-left corner of every slide (except title slide where it appears center-right area)
- **Copyright text**: Bottom-right corner — `© National Telecom All Rights Reserved`
- **Logo on white bg slides**: Use the lockup matching the audience/formality per the table above
- **Logo on yellow bg slides**: See "Known gap" above — use `NT_1_v3.png` and treat as a temporary workaround

### Prohibited Logo Usage

- NEVER place the logo on black or dark backgrounds
- NEVER distort or recolor the logo
- NEVER use dark/black background logo variants — none are provided, and none should be improvised

---

## Visual Motif: The "Vital Sign" Icon Family

The NT brand identity's rounded pill/capsule shapes come directly from the NT icon mark — an audio-waveform-style arrangement of dots and bars, referred to in the brand assets as the "Vital Sign" family. Four real variants are bundled at `assets/graphic-elements/`:

| File | Description | Use When |
|------|-------------|----------|
| `v2_Vital_Sign.png` | Full symmetric arrangement — dot, bar, tall center bar, bar, dot (mirrored both sides) | General decorative motif, title slides, backgrounds |
| `v2_Next_Vital_Sign.png` | Asymmetric variant — the exact icon used inside the official logo lockups | Anywhere the icon needs to read as "the NT mark" specifically (headers, icon-only branding) — **always use at full 100% color, per the gradient rule's graphic-element exception** |
| `v2_Single_Sign.png` | One tall bar/pill alone | Minimal accent marker, single visual anchor |
| `v2_Dot_Sign.png` | One dot alone | Smallest accent marker, bullet-style marker |

Pixel-sampled confirmation: the yellow in all four files is `#FFD100` (255, 209, 0) — matches the official brand hex exactly, no correction needed.

**Prefer inserting these real PNG files** (via the image APIs in Codex presentation tooling, or by duplicating a template slide/layout that already contains one) over hand-drawing approximate pill shapes — they're the actual brand asset, not a redrawn approximation.

When hand-drawing pill shapes is still necessary (e.g. custom card containers, content backgrounds that aren't literally the icon mark):
- **Decorative background elements**: Light yellow (`#FFD100` with transparency — 10% opacity minimum — or a lighter gradient tint) pill shapes on white backgrounds
- **Content containers**: Yellow pill shapes that can hold cityscape imagery or solid fills
- **Card shapes**: Tall rounded rectangles used as content columns (see slide 7 / Layout 6)
- **Accent elements**: Small yellow rounded bars used as visual markers

In JavaScript presentation code, translate these geometry values to the active API:
```javascript
// Pill shape (rounded rectangle with maximum radius) — for custom containers only,
// not a substitute for the real icon files above
const pillShape = {
    shape: "rounded-rectangle",
    x: 0.5, y: 1.5, w: 2, h: 5,
    fill: { color: "FFD100" },
    radius: 0.5  // Large radius for pill effect
};
```

---

## Slide Structure Standards

### Every Content Slide Must Have

1. **NT Logo** — bottom-left corner
2. **Copyright** — bottom-right: `© National Telecom All Rights Reserved`
3. **Slide number** — near copyright area (bottom-right)
4. **No black backgrounds** — white or yellow only

### Recommended Slide Sequence

1. **Title Slide** (Layout 0: "Title Slide") — White bg, decorative pill graphic left, NT logo center-right, title text bottom-right
2. **Section Divider** (Layout 1: "Custom Layout") — Yellow bg (#FFD100), title text right side
3. **Content Slides** (Layouts 2–9) — Various white/yellow layouts with content areas
4. **Closing Slide** (Layout 11: "8_Custom Layout") — Yellow bg with cityscape, NT logo + company info

### Available Layouts in Template

| Layout Index | Name | Background | Best For |
|--------------|------|------------|----------|
| 0 | Title Slide | White | Opening/cover slide |
| 1 | Custom Layout | Yellow (#FFD100) | Section divider with title |
| 2 | 1_Custom Layout | White | Content with right-side text |
| 3 | 2_Custom Layout | White | Two-column: image left + text blocks right |
| 4 | 3_Custom Layout | White | Text content with right-side cityscape image |
| 5 | 4_Custom Layout | White | Empty with pill accent (minimal) |
| 6 | 5_Custom Layout | White | Multi-image showcase (4 tall pills) |
| 7 | 6_Custom Layout | White | Four-column card layout (4 pill cards) |
| 8 | 7_Custom Layout | White | Minimal with yellow accent bar top-left |
| 9 | 9_Custom Layout | Yellow (#FFD100) | Yellow bg with white header banner |
| 10 | 10_Custom Layout | White + Yellow | White header + yellow body |
| 11 | 8_Custom Layout | Yellow (#FFD100) | Closing slide with company info |

For complete placeholder positions and content mapping, read `references/layouts.md`.

---

## Applying NT Style When Creating from Scratch

When not using the template, apply these standards in every slide created with Codex presentation tooling:

```javascript
// Use LAYOUT_WIDE / 13.333" x 7.5" and set the deck author to "National Telecom".

// -- Brand constants --
const NT_YELLOW = "FFD100";     // Official NT Yellow (PANTONE 109 C)
const NT_WHITE = "FFFFFF";
const NT_BLACK = "000000";
const NT_DARK = "212121";
const NT_GRAY = "545859";
const NT_MID_GRAY = "888888";
// -- Recommended secondary palette (pair with NT_YELLOW, don't use standalone) --
const NT_TEAL = "40C1AC";
const NT_DARK_GREY = "545859";
const NT_BRICK_RED = "E1523E";
const NT_BROWN = "924C2E";
const FONT_NT = "NT";           // Family name from bundled NT_Bold/NT_Regular files

// -- Standard footer for every content slide --
function addFooter(slide) {
    // Copyright text (bottom-right)
    slide.addText("© National Telecom All Rights Reserved", {
        x: 9.0, y: 7.05, w: 4.0, h: 0.35,
        fontSize: 8, fontFace: FONT_NT, bold: false, color: NT_BLACK,
        align: "right"
    });
    // Add NT logo bottom-left with the presentation tool's image API.
    // Use path: `${NT_SKILL_DIR}/assets/logos/NT_2_v3.png`.
}
```

---

## Prohibited Elements

- **NO black backgrounds** on any slide
- **NO dark-themed slides** — always white or yellow
- **NO accent lines under titles** (AI-generated hallmark — use whitespace instead)
- **NO generic blue color schemes** — NT brand is yellow-dominant
- **NO distorted or recolored logos**
- **NO unapproved font substitutions** without fallback chain (NT Bold → Helvetica Neue Medium → Arial)
- **NO dark/black background logo variants** — none exist; see "Known gap" in Logo Usage

---

## File Assets

**Fonts** (`assets/fonts/`) — real NT typeface files; see Typography section for Codex font install steps
- `NT_Bold.ttf` — family `NT`, style `Bold`
- `NT_Regular.ttf` — family `NT`, style `Regular`

**Logos** (`assets/logos/`) — official lockups; see Logo Usage section for which to use when
- `NT_1_v3.png` — icon + "nt" only (746×497)
- `NT_2_v3.png` — icon + "nt" + English company name (1225×551)
- `NT_3_v3.png` — icon + "nt" + Thai company name (1230×514)
- `NT_4_v3.png` — icon + "nt" + Thai + English, full lockup (2755×529)

**Graphic elements** (`assets/graphic-elements/`) — the "Vital Sign" icon family; see Visual Motif section
- `v2_Vital_Sign.png` — full symmetric icon
- `v2_Next_Vital_Sign.png` — asymmetric variant, the exact mark used inside the logo lockups
- `v2_Single_Sign.png` — single bar
- `v2_Dot_Sign.png` — single dot

**Template**
- `NT_Presentation_Template.pptx` — official NT template, 12 layouts / 11 example slides, recolored to `#FFD100`. Use as the template source for the editing workflow.

Embedded images within the template itself (older, approximate placeholders — prefer the real files above for new work):
- `image2.png` — small dark NT logo (125×50)
- `image3.png` — full NT logo (482×196)
- `image4.png` — decorative pill shapes with cityscape (978×738) for title slide
- `image7.jpeg` — cityscape background photo (2822×1650) for closing slide

To extract images from the template itself, unzip the .pptx and find them in `ppt/media/`.
