---
name: nt-brand-guidelines
description: Applies NT (National Telecom) official brand colors, typography, and layout standards to PowerPoint presentations and other NT-branded visuals such as dashboards, charts, and reports. Use this skill whenever creating or styling slides for NT, including any mention of "NT template", "NT slides", "NT presentation", "NT style", "NT brand", "NT deck", or when the user asks to create presentation slides in the NT corporate format. Also trigger when editing an existing NT-branded presentation, when choosing colors or fonts for an NT dashboard or chart, or when a logo/icon/font for NT is needed. This skill ensures correct use of NT yellow (#FFD100, PANTONE 109C), the recommended secondary palette (teal, dark grey, brick red, brown), the real bundled NT Bold/NT Regular font files, the four official logo lockups, the "Vital Sign" icon family, LAYOUT_WIDE dimensions, proper logo placement, and the signature rounded pill-shape visual motif.
---

# NT (National Telecom) Brand Styling for Presentations

## Overview

This skill provides NT's official brand identity specifications for creating PowerPoint slide decks. It bundles the official NT presentation template and defines all visual rules: colors, fonts, slide dimensions, logo usage, layout patterns, and prohibited elements.

**Keywords**: NT, National Telecom, NT template, NT slides, NT brand, NT presentation, corporate identity, Thai telecom, brand colors, slide styling, NT Bold, NT Regular, yellow branding

## Quick Start

Resolve bundled files relative to this skill directory. When scripting, set `NT_SKILL_DIR` to the absolute path of this folder and build asset paths from that value.

There are two ways to create NT-branded presentations:

1. **Template-based editing** (recommended for speed): Use the bundled template at `assets/NT_Presentation_Template.pptx` as the source deck: inspect the master/layout hierarchy, duplicate or reuse selected layouts, fill placeholders locally, and render every final slide for visual QA. In Claude, follow the pptx skill's editing workflow; in Codex, use the `Presentations` skill's template-following workflow.

2. **Create from scratch** (for full control): Apply the brand specifications below with the platform's presentation tooling: PptxGenJS through the pptx skill in Claude, or `@oai/artifact-tool` from the `Presentations` skill in Codex. With any other PPTX library, translate these constants and layout rules to it.

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
| **Dark Grey** | 425 C | `#545859` | 63, 51, 45, 33 |
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

**To make these render correctly (not fall back) when generating or QA-rendering a .pptx in a sandboxed or fresh environment (Claude's container, Codex)**, install them into the local font cache before creating slides or running visual QA:

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
When filling template placeholders, explicitly set the font to family "NT" (the template's "NT Bold"/"NT Regular" face names do not resolve in LibreOffice). For Thai text, also set the complex-script (cs) typeface to "NT"; most libraries, including python-pptx's font.name, set only the Latin typeface.

If the font isn't installed in the environment (e.g. a fresh session where the install step was skipped), LibreOffice will substitute a fallback for QA preview purposes only — the fallback chain below still applies for that case, and for recipients opening the file on a machine without the NT font installed.

### Effective Size — NT renders smaller than normal fonts at the same point size

**Verified finding**: at an identical point size, text set in NT Bold/NT Regular reads visually smaller than text set in a normal font (Arial, Calibri, Helvetica). This is a real, measurable difference in the typeface's own metrics — not a rendering bug, not per-machine — so it applies every time NT is used and must be compensated for by setting NT text **larger** than you would size a normal font for the same visual weight.

**Why**: how big text *looks* at a given point size is driven mainly by **x-height** (the height of lowercase letters like "n", "o", "x") relative to the font's em square — not the nominal point size alone. NT's x-height is meaningfully smaller, as a fraction of its em square, than Arial's or Calibri's, so `fontSize: 14` in NT visibly reads smaller than `fontSize: 14` in the fallback fonts.

Measured directly from the bundled font files with `fontTools` (`OS/2.sxHeight` / `OS/2.sCapHeight`, normalized by `unitsPerEm`, cross-checked against glyph bounding boxes for `n`/`o`/`H`/`A`):

| Font | x-height ratio | cap-height ratio |
|------|-----------------|-------------------|
| **NT Regular / NT Bold** | **0.376** | 0.485 |
| Carlito (Calibri-compatible fallback) | 0.478 | 0.642 |
| Liberation Sans (Arial-compatible fallback) | 0.528 | 0.688 |

This confirms field-reported experience (NT sitting at ~0.375 vs. a normal font at ~0.51 on the same size scale) — the reported "normal font" number lines up with the Arial-compatible measurement above.

**Compensation factor** — to make NT-set text look the same visual size as the same nominal point size would in a normal font, scale the point size up by:
- **~1.27–1.32×** when matching against Calibri / Helvetica Neue Medium
- **~1.36–1.42×** when matching against Arial
- **~1.3–1.4× as a general-purpose multiplier** when the specific fallback doesn't matter

**Practical rule**: whenever a source spec, a client's original deck, or a generic sizing convention gives a point size assumed for a normal font, multiply by **~1.3–1.4×** before applying it to NT Bold/NT Regular. Example: body text speced at 14pt in a normal font → set `fontSize: 18–19` in NT Regular to read as equivalent size. This applies to every element — titles, body, captions, chart/legend text, table cells — not just headline sizes. Treat the multiplier as a target, not an absolute: in tight/dense layouts (data tables, multi-column cards, legends) where full compensation would overflow the available space, it's fine to compensate partially rather than not at all — but never size NT at the same nominal point size as a normal-font spec and assume it will look the same, and always verify by rendering to PDF/PNG and eyeballing the actual result, especially at small sizes where rounding matters most.

### Font Families

| Role | Font | Fallback |
|------|------|----------|
| **Headings / Titles** | NT Bold | Helvetica Neue Medium → Arial Black → Arial |
| **Body Text** | NT Regular | Helvetica Neue Medium → Calibri → Arial |
| **Secondary** | Helvetica Neue Medium | Calibri |

### Size Guidelines

The **Nominal Size** column below is standard presentation sizing, as commonly used with a normal font (Arial/Calibri). The **NT-Compensated Size** column applies the ~1.3–1.4× factor from "Effective Size" above and is what to actually set when the text is in NT Bold/NT Regular.

| Element | Nominal Size (normal font) | NT-Compensated Size | Weight |
|---------|------|------|--------|
| Slide title | 28–36pt | ~36–50pt | NT Bold |
| Section header / subtitle | 20–24pt | ~26–34pt | NT Bold |
| Body text | 14–16pt | ~18–22pt | NT Regular |
| Captions / footnotes | 10–12pt | ~13–17pt | NT Regular, color `#888888` |
| Large stat callouts | 48–72pt | ~62–101pt | NT Bold |
| Copyright footer | 8–10pt | ~10–14pt | NT Regular, color `#000000` |

In space-constrained layouts (dense tables, multi-column cards, small legends) the full compensated size may not fit — see the "Treat the multiplier as a target, not an absolute" note above. Prioritize fitting and legibility over hitting the top of the compensated range, but still size up from the nominal column rather than using it as-is.

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

Use a wide 16:9 PowerPoint canvas matching 13.333" x 7.5" in whichever tool builds the deck (in Codex, the `Presentations` workflow). If the library exposes PowerPoint layout constants, choose `LAYOUT_WIDE`:

```javascript
// PptxGenJS
pres.layout = "LAYOUT_WIDE";  // 13.333" × 7.5"
```

```python
# python-pptx (EMU values)
prs.slide_width = 12192000   # 13.333 inches
prs.slide_height = 6858000   # 7.5 inches
```

---

## Logo Usage

### Official Logo Lockups (bundled, real assets)

Four official lockups are bundled at `assets/logos/`. All four use the same icon mark (`#FFD100` yellow bars) + `#545859` dark grey wordmark, on a transparent/white background. Pixel sampling confirms these exact values in `NT_1_v3.png`, `NT_2_v3.png` and `NT_4_v3.png`; `NT_3_v3.png` samples slightly off (`#FDD209` yellow, `#55595B` grey). Use it as it is; do not recolor it.

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
- **Yellow placement:** keep NT Yellow #FFD100 visually dominant through the frame (header band, title bar, sidebar, section markers), not behind tables or charts. Also use it for interactive and selected states.
- **Accent contrast:** #FFD100 on white or near-white is only ~1.4:1, below the 3:1 WCAG minimum for UI components. Active filters, tabs, and buttons must be a yellow fill with #000000 text (14.4:1), or pair the yellow with a #545859 or #000000 outline or indicator.
- **Text and backgrounds:** text #000000 or #212121; backgrounds white #FFFFFF or NT Yellow. No dark mode.
- **Chart palette:** NT Yellow plus Teal #40C1AC, Dark Grey #545859, Brick Red #E1523E, Brown #924C2E (5 colors). Do not place Teal and Brick Red adjacent; run a color-blindness simulation before finalizing.
- **Do not use:** generic blue accents (including the common #2272B4 fallback) or any color outside the NT palette.
- **Fonts:** family "NT" with bold on/off, scaled up ~1.3–1.4x versus Arial/Calibri sizing, with the fallback chain in the Typography section. If the platform cannot load a custom font, use the fallback chain.

## Dashboards and Data Views

The color, font, and prohibition rules above apply to dashboards, charts, and reports on any platform (Excel, HTML, Power BI, Databricks AI/BI), not only slides. When a generic dashboard-design guideline conflicts with this section, this section wins.

- **Native charts:** the template's theme accent colors are still Office defaults (accent1 #5B9BD5 blue). Always set chart series colors explicitly to the NT palette; never rely on theme defaults.
--- 

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

Pixel sampling: the yellow in all four files is `#FDD209` (253, 210, 9), a near match to the official `#FFD100` rather than an exact one. Use the files as they are, and use `#FFD100` for any shape drawn in code.

**Prefer inserting these real PNG files** (via the presentation tool's image API, such as `addImage` in PptxGenJS, or by duplicating a template slide/layout that already contains one) over hand-drawing approximate pill shapes — they're the actual brand asset, not a redrawn approximation.

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
// PptxGenJS equivalent: slide.addShape(pres.shapes.ROUNDED_RECTANGLE, { x, y, w, h, fill, rectRadius: 0.5 })
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
3. **Content Slides** (Layouts 2–4, 6–10; avoid Layout 5)
4. **Closing Slide** (Layout 11: "8_Custom Layout") — Yellow bg with cityscape, NT logo + company info

### Available Layouts in Template

| Layout Index | Name | Background | Best For |
|--------------|------|------------|----------|
| 0 | Title Slide | White | Opening/cover slide |
| 1 | Custom Layout | Yellow (#FFD100) | Section divider with title |
| 2 | 1_Custom Layout | White | Content with right-side text |
| 3 | 2_Custom Layout | White | Two-column: image left + text blocks right |
| 4 | 3_Custom Layout | White | Text content with right-side cityscape image |
| 5 | 4_Custom Layout | White | Fixed four-item list with Latin filler text — do not use for new content (see layouts.md) |
| 6 | 5_Custom Layout | White | Text left + fixed decorative pill images |
| 7 | 6_Custom Layout | White | Four-column card layout (4 pill cards) |
| 8 | 7_Custom Layout | White | Minimal with yellow accent bar top-left |
| 9 | 9_Custom Layout | Yellow (#FFD100) | Yellow bg with white header banner |
| 10 | 10_Custom Layout | White + Yellow | Yellow header band + white body (good for data-heavy slides) |
| 11 | 8_Custom Layout | Yellow (#FFD100) | Closing slide with company info |

For complete placeholder positions and content mapping, read `references/layouts.md`.

---

## Applying NT Style When Creating from Scratch

When not using the template, apply these standards in every slide. The code uses PptxGenJS-style calls; translate them to the active presentation API:

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
        x: 8.66, y: 7.05, w: 4.0, h: 0.35,   // right edge 12.66", matches template
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

**Fonts** (`assets/fonts/`) — real NT typeface files; see Typography section for font install steps
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
