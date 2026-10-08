# NT Template Layout Reference

Detailed specifications for each slide layout in the NT Presentation Template (`assets/NT_Presentation_Template.pptx`).
All coordinates are in inches, measured from the template file itself (x, y = top-left corner). Slide dimensions: 13.333" × 7.5" (LAYOUT_WIDE).

## Contents

- How to read this reference
- Layout 0: Title Slide
- Layout 1: Custom Layout (Section Divider – Yellow)
- Layout 2: 1_Custom Layout (Content with Right Text)
- Layout 3: 2_Custom Layout (Image Left + Text Right)
- Layout 4: 3_Custom Layout (Text Left + Cityscape Right)
- Layout 5: 4_Custom Layout (Fixed Four-Item List – do not use for new content)
- Layout 6: 5_Custom Layout (Text Left + Fixed Pill Images)
- Layout 7: 6_Custom Layout (Four-Column Cards)
- Layout 8: 7_Custom Layout (Minimal with Accent Bar)
- Layout 9: 9_Custom Layout (Yellow BG with White Header Band)
- Layout 10: 10_Custom Layout (White BG with Yellow Header Band)
- Layout 11: 8_Custom Layout (Closing Slide)
- Common Footer Positioning
- Content Area Safe Zones

---

## How to read this reference

- **Title placeholders are BODY-type placeholders, not TITLE-type.** Address them by `idx`, not by a title accessor (in python-pptx, `slide.shapes.title` returns `None` on these layouts).
- **The title placeholder is `idx=1` on every layout except Layout 4**, where the title is `idx=21` and the body is `idx=1`.
- Shapes listed as "fixed" are part of the layout itself. They appear on every slide that uses the layout and cannot be replaced through placeholders.
- Background: the master background is white `#FFFFFF`. Layouts 1, 9 and 11 override it with solid `#FFD100`.
- Default text color in placeholders is `#000000` (inherited from the master), except the Layout 0 title placeholder, which is set to `#545859`.

---

## Layout 0: Title Slide

**Background**: White
**Purpose**: Opening / cover slide
**Visual**: Fixed decorative pill-shaped cityscape graphic on the left, large NT logo center-right, title text below the logo

| Element | Position (x, y) | Size (w, h) | Notes |
|---------|-----------------|-------------|-------|
| Title text (idx=1) | 7.74", 3.86" | 4.42", 0.98" | NT Bold, default color `#545859` |
| Decorative graphic (fixed) | 0.56", 1.66" | 5.55", 4.19" | `image4.png` — pill shapes with cityscape |
| NT logo (fixed) | 8.40", 2.41" | 3.19", 1.30" | `image3.png` |
| Copyright (fixed) | 11.44", 7.24" | 1.74", 0.14" | `© National Telecom All Rights Reserved` |

**Placeholders**: Body (idx=1) only. No slide number and no bottom-left logo on this layout.

---

## Layout 1: Custom Layout (Section Divider – Yellow)

**Background**: Solid yellow `#FFD100`
**Purpose**: Section divider / chapter title
**Visual**: Fixed group of semi-transparent white pill shapes on the left, title at upper right of center

| Element | Position (x, y) | Size (w, h) | Notes |
|---------|-----------------|-------------|-------|
| Title text (idx=1) | 4.50", 0.44" | 4.50", 0.79" | NT Bold, `#000000` on yellow |
| Decorative pills (fixed group) | -0.69", 1.74" | 7.95", 6.00" | White pills, translucent |
| NT logo (fixed) | 0.16", 7.05" | 0.87", 0.35" | `image2.png` |
| Slide number (idx=2) | 12.87", 7.14" | 0.21", 0.24" | `#000000` |
| Copyright (fixed) | 10.92", 7.20" | 1.74", 0.14" | — |

**Placeholders**: Body (idx=1), Slide Number (idx=2)

---

## Layout 2: 1_Custom Layout (Content with Right Text)

**Background**: White
**Purpose**: Title with decorative light-yellow pills on the left and open space on the right
**Visual**: Same pill arrangement as Layout 1, in light yellow on white

| Element | Position (x, y) | Size (w, h) | Notes |
|---------|-----------------|-------------|-------|
| Title text (idx=1) | 4.50", 0.44" | 4.50", 0.79" | NT Bold, `#000000` |
| Decorative pills (fixed group) | 0.00", 1.74" | 7.26", 5.76" | Light-yellow pills |
| NT logo (fixed) | 0.16", 7.05" | 0.87", 0.35" | `image2.png` |
| Slide number (idx=2) | 12.87", 7.14" | 0.21", 0.24" | Small yellow marker shape behind it |
| Copyright (fixed) | 10.92", 7.20" | 1.74", 0.14" | — |

**Placeholders**: Body (idx=1), Slide Number (idx=2). There is no body-text placeholder; add content manually.
**Content area**: below y = 1.74", place content to the right of the pill group (x ≥ 7.3"). Above y = 1.74" the area from x = 4.5" is clear. Render to confirm nothing overlaps the pills.

---

## Layout 3: 2_Custom Layout (Image Left + Text Right)

**Background**: White
**Purpose**: Two-column layout — picture on the left, two text blocks stacked on the right
**Visual**: Tall yellow bar at the far left, picture area center-left, a short yellow bar beside each text block

| Element | Position (x, y) | Size (w, h) | Notes |
|---------|-----------------|-------------|-------|
| Title text (idx=1) | 0.66", 0.44" | 4.39", 0.79" | NT Bold, `#000000` |
| Picture placeholder (idx=23) | 0.70", 1.81" | 5.74", 4.79" | For image content |
| Text block 1 (idx=21) | 8.00", 2.29" | 4.00", 1.41" | NT Regular body text |
| Text block 2 (idx=22) | 8.00", 4.46" | 3.99", 1.41" | NT Regular body text |
| Yellow bar, left (fixed) | 0.57", 2.07" | 0.27", 4.15" | Decorative |
| Yellow bars beside text (fixed) | 6.95", 2.34" and 6.95", 4.46" | 0.71", 1.41" each | Aligned with text blocks 1 and 2 |
| NT logo (fixed) | 0.13", 7.02" | 0.89", 0.36" | `image3.png` |

**Placeholders**: Body (idx=1), Body (idx=21), Body (idx=22), Picture (idx=23), Slide Number (idx=2)

---

## Layout 4: 3_Custom Layout (Text Left + Cityscape Right)

**Background**: White
**Purpose**: Text content on the left, fixed yellow-tinted cityscape in a rounded shape on the right half
**Visual**: Text area left, cityscape image fills the right half edge to edge

| Element | Position (x, y) | Size (w, h) | Notes |
|---------|-----------------|-------------|-------|
| Title text (**idx=21**) | 0.66", 0.44" | 4.38", 0.79" | NT Bold, `#000000` |
| Body text (**idx=1**) | 0.66", 1.61" | 4.68", 4.46" | NT Regular, `#000000` |
| Cityscape image (fixed) | 6.68", 0.00" | 6.66", 7.50" | `image1.png` |
| NT logo (fixed) | 0.13", 7.02" | 0.89", 0.36" | `image3.png` |

**Placeholders**: Body (idx=21) for the **title**, Body (idx=1) for the **content**, Slide Number (idx=2). This is the only layout where the title is not idx=1.

---

## Layout 5: 4_Custom Layout (Fixed Four-Item List – do not use for new content)

**Background**: White
**Visual**: Cityscape image in a half-round shape on the left half, a yellow arc with four dots, and **four fixed text boxes containing placeholder Latin text ("Vestibulum semper eros…")** on the right

| Element | Position (x, y) | Size (w, h) | Notes |
|---------|-----------------|-------------|-------|
| Cityscape image (fixed) | 0.00", 0.00" | 6.66", 7.50" | `image1.png` |
| Yellow arc (fixed) | -1.07", -0.30" | 8.10", 8.10" | Large half-round outline |
| Four dots (fixed) | x 6.42"–6.88", y 1.82" / 3.07" / 4.32" / 5.57" | 0.24" each | Along the arc |
| Four text boxes (fixed, Latin filler text) | x 7.03"–7.40", y 1.28" / 2.56" / 3.89" / 5.16" | 4.53", 1.04" each | **Not placeholders** |
| NT logo (fixed) | 0.16", 7.05" | 0.87", 0.35" | `image2.png` |

**Placeholders**: Slide Number (idx=2) only.

**Warning**: the four filler text boxes are layout shapes, so they render on every slide built from this layout and cannot be filled through placeholders. Do not use this layout for charts, diagrams or freeform content — use Layout 8 instead. Use Layout 5 only after editing the layout itself to remove or replace those text boxes.

---

## Layout 6: 5_Custom Layout (Text Left + Fixed Pill Images)

**Background**: White
**Purpose**: Title and text on the left, decorative staggered pill images across the slide
**Visual**: Four tall pill-shaped cityscape images at staggered heights; the third from the left is yellow-tinted, the other three are light grey. Some pills extend past the slide edges and are cropped.

| Element | Position (x, y) | Size (w, h) | Notes |
|---------|-----------------|-------------|-------|
| Title text (idx=1) | 0.66", 0.44" | 4.42", 0.79" | NT Bold, `#000000` |
| Body text (idx=21) | 0.66", 1.62" | 4.68", 4.46" | NT Regular |
| Pill image 1 (fixed, grey) | 1.93", 4.26" | 1.97", 6.17" | `image6.png`, extends below slide |
| Pill image 2 (fixed, grey) | 4.80", 2.46" | 1.97", 6.17" | `image6.png`, extends below slide |
| Pill image 3 (fixed, yellow) | 7.66", 0.72" | 1.97", 6.18" | `image5.png` |
| Pill image 4 (fixed, grey) | 10.52", -0.97" | 1.97", 6.17" | `image6.png`, extends above slide |
| NT logo (fixed) | 0.13", 7.02" | 0.89", 0.36" | `image3.png` |

**Placeholders**: Body (idx=1), Body (idx=21), Slide Number (idx=2). There are no picture placeholders; the pill images are fixed and cannot be swapped from the slide.
**Overlap note**: pill images 1 and 2 overlap the lower part of the body placeholder (from y = 4.26" at x 1.93"–3.90", and from y = 2.46" at x 4.80"–5.34"). Keep body text short and near the top, and render to confirm.

---

## Layout 7: 6_Custom Layout (Four-Column Cards)

**Background**: White
**Purpose**: Four equal yellow pill cards in a row, each with a header and a short description
**Visual**: Title at top center, full-width subtitle, four yellow pills below with text inside

| Element | Position (x, y) | Size (w, h) | Notes |
|---------|-----------------|-------------|-------|
| Title text (idx=1) | 4.50", 0.44" | 4.56", 0.79" | NT Bold, `#000000` |
| Subtitle (idx=21) | 0.70", 1.48" | 11.95", 1.21" | NT Regular |
| Yellow pill cards (fixed) | x 0.70" / 4.17" / 7.65" / 11.12", y 3.42" | 1.51", 3.53" each | Bottom edge at 6.95" |
| Card 1 header (idx=26) | 0.77", 4.41" | 1.38", 0.42" | NT Bold in pill |
| Card 1 body (idx=22) | 0.72", 5.07" | 1.48", 0.71" | NT Regular in pill |
| Card 2 header (idx=27) | 4.24", 4.41" | 1.38", 0.42" | NT Bold in pill |
| Card 2 body (idx=23) | 4.18", 5.07" | 1.49", 0.71" | NT Regular in pill |
| Card 3 header (idx=28) | 7.72", 4.41" | 1.38", 0.42" | NT Bold in pill |
| Card 3 body (idx=24) | 7.67", 5.07" | 1.48", 0.71" | NT Regular in pill |
| Card 4 header (idx=29) | 11.15", 4.41" | 1.48", 0.44" | NT Bold in pill |
| Card 4 body (idx=25) | 11.15", 5.07" | 1.47", 0.67" | NT Regular in pill |
| NT logo (fixed) | 0.13", 7.02" | 0.89", 0.36" | `image3.png` |

**Placeholders**: Body (idx=1) title, idx=21 subtitle, idx=22–25 card bodies (left to right), idx=26–29 card headers (left to right), Slide Number (idx=2). Card text boxes are narrow (about 1.5"); keep headers to one or two words and bodies to a few short lines.

---

## Layout 8: 7_Custom Layout (Minimal with Accent Bar)

**Background**: White
**Purpose**: Clean, open layout — the recommended layout for charts, tables, diagrams and freeform content
**Visual**: Single short yellow vertical bar at top-left, otherwise empty

| Element | Position (x, y) | Size (w, h) | Notes |
|---------|-----------------|-------------|-------|
| Title text (idx=1) | 0.39", 0.29" | 4.33", 0.79" | NT Bold, `#000000` |
| Yellow accent bar (fixed) | 0.19", 0.22" | 0.10", 0.94" | Rounded |
| NT logo (fixed) | 0.13", 7.02" | 0.89", 0.36" | `image3.png` |
| Slide number (idx=2) | 12.88", 7.18" | 0.21", 0.24" | — |

**Placeholders**: Body (idx=1), Slide Number (idx=2)

---

## Layout 9: 9_Custom Layout (Yellow BG with White Header Band)

**Background**: Solid yellow `#FFD100`
**Purpose**: Yellow content slide with a white header band at the top
**Visual**: Two white rounded bands across the top (a long band holding the title and a short band to its right), yellow body below

| Element | Position (x, y) | Size (w, h) | Notes |
|---------|-----------------|-------------|-------|
| White header band, long (fixed) | 0.00", 0.23" | 9.83", 0.91" | — |
| White header band, short (fixed) | 9.92", 0.23" | 3.41", 0.91" | — |
| Title text (idx=1) | 0.39", 0.29" | 4.33", 0.79" | NT Bold, `#000000`, inside the white band |
| Body text (idx=21) | 0.66", 1.62" | 12.06", 5.00" | NT Regular, `#000000` on yellow |
| NT logo (fixed) | 0.16", 7.05" | 0.87", 0.35" | `image2.png` |

**Placeholders**: Body (idx=1), Body (idx=21), Slide Number (idx=2)

---

## Layout 10: 10_Custom Layout (White BG with Yellow Header Band)

**Background**: White
**Purpose**: White content slide with a yellow header band — the color-inverse of Layout 9
**Visual**: Two yellow `#FFD100` rounded bands across the top (same geometry as Layout 9), white body below

| Element | Position (x, y) | Size (w, h) | Notes |
|---------|-----------------|-------------|-------|
| Yellow header band, long (fixed) | 0.00", 0.23" | 9.83", 0.91" | `#FFD100` |
| Yellow header band, short (fixed) | 9.92", 0.23" | 3.41", 0.91" | `#FFD100` |
| Title text (idx=1) | 0.39", 0.29" | 4.33", 0.79" | NT Bold, `#000000`, inside the yellow band |
| Body text (idx=21) | 0.66", 1.62" | 12.06", 5.00" | NT Regular, `#000000` on white |
| NT logo (fixed) | 0.13", 7.02" | 0.89", 0.36" | `image3.png` |

**Placeholders**: Body (idx=1), Body (idx=21), Slide Number (idx=2). Suitable for data-heavy slides: the yellow frame keeps brand presence while the content sits on white.

---

## Layout 11: 8_Custom Layout (Closing Slide)

**Background**: Yellow `#FFD100` with a full-bleed yellow-tinted cityscape image
**Purpose**: Final/closing slide with company information
**Visual**: Two white rounded shapes across the middle — the left one holds the NT logo, the right one holds the company text

Fixed content (embedded in layout):

| Element | Position (x, y) | Size (w, h) | Notes |
|---------|-----------------|-------------|-------|
| Cityscape background | 0.01", -0.17" | 13.33", 7.67" | `image7.jpeg` |
| White shape, left | -0.02", 2.36" | 5.24", 3.11" | Holds the logo |
| NT logo | 0.69", 3.24" | 3.32", 1.35" | `image3.png` |
| White shape, right | 5.69", 2.36" | 7.65", 3.11" | Holds the company text |
| Company name text | 6.89", 3.06" | 5.79", 0.91" | บริษัท โทรคมนาคมแห่งชาติ จำกัด (มหาชน) / National Telecom Public Company Limited |
| Yellow separator bar | 6.69", 4.07" | 6.08", 0.09" | — |
| Website / contact text | 6.94", 4.22" | 5.70", 0.53" | www.ntplc.co.th \| Contact Center 1888 |

**Placeholders**: Slide Number (idx=2) at 6.44", 6.75" (3.11" × 0.40") only — all other content is pre-built into the layout.

---

## Common Footer Positioning

For all content slides (Layouts 1–10). These elements are already built into each layout; add them manually only when building slides from scratch.

| Element | Position (x, y) | Size (w, h) | Notes |
|---------|-----------------|-------------|-------|
| NT logo (Layouts 1, 2, 5, 9) | 0.16", 7.05" | 0.87", 0.35" | `image2.png` |
| NT logo (Layouts 3, 4, 6, 7, 8, 10) | 0.13", 7.02" | 0.89", 0.36" | `image3.png` |
| Copyright text | 10.92", 7.20" (7.24" on Layouts 8–10) | 1.74", 0.14" | Right edge at 12.66" |
| Slide number (idx=2) | 12.84"–12.88", 7.13"–7.18" | ~0.21", 0.24" | Small yellow marker shape behind it on Layouts 2, 3, 4, 5, 8, 10 |

When adding a footer from scratch, keep the copyright text's right edge at or before 12.7" so it does not overlap the slide number.

---

## Content Area Safe Zones

When creating slides from scratch, keep content within these bounds:

| Slide Type | Content Area |
|------------|-------------|
| Full-width content (Layouts 8, 9, 10) | x: 0.5"–12.8", y: 1.3"–6.8" (below the title / header band) |
| Left column (Layout 4, cityscape on right) | x: 0.5"–6.4", y: 0.3"–6.8" |
| Right side (Layout 2, pills on left) | x: 7.3"–12.8" for y below 1.74"; x: 4.5"–12.8" above it |
| Title area (Layouts 3, 4, 6, 8, 9, 10) | x: 0.4"–5.0", y: 0.3"–1.2" |
| Footer reserved zone | y: 6.8"–7.5" (do not place content here) |

Layout 7's fixed card shapes extend to y = 6.95", into the footer zone, by design; do not add further content below the cards.
