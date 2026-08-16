# NT Template Layout Reference

Detailed specifications for each slide layout in the NT Presentation Template.
All coordinates are in inches. Slide dimensions: 13.333" × 7.5" (LAYOUT_WIDE).

---

## Layout 0: Title Slide

**Background**: White
**Purpose**: Opening / cover slide
**Visual**: Decorative yellow pill shapes with cityscape image on left half, NT logo center-right

| Element | Position (x, y) | Size (w, h) | Notes |
|---------|-----------------|-------------|-------|
| Title text | 7.74", 3.86" | 4.42", 0.98" | NT Bold, white or black depending on design |
| Decorative graphic | Left half | ~6.5" wide | `image4.png` — pill shapes with cityscape |
| NT Logo | Center-right | — | `image3.png` large logo |
| Copyright | Bottom-right | — | Small text |

**Placeholders**: Body (idx=1) at bottom-right for title/subtitle text.

---

## Layout 1: Custom Layout (Section Divider – Yellow)

**Background**: Solid yellow `#FFD100`
**Purpose**: Section divider / chapter title
**Visual**: Yellow background with subtle lighter pill shapes on left, title on right side

| Element | Position (x, y) | Size (w, h) | Notes |
|---------|-----------------|-------------|-------|
| Title text | 4.50", 0.44" | 4.55", 0.79" | NT Bold, `#000000` on yellow bg |
| Slide number | Bottom-right | — | Small |
| NT Logo | Bottom-left | — | `image2.png` (dark logo for yellow bg) |
| Copyright | Bottom-right | — | `© National Telecom All Rights Reserved` |

**Placeholders**: Body (idx=1), Slide Number (idx=2)

---

## Layout 2: 1_Custom Layout (Content with Right Text)

**Background**: White
**Purpose**: General content with decorative pills on left, content area on right
**Visual**: Light yellow pill shapes on left side, content on right half

| Element | Position (x, y) | Size (w, h) | Notes |
|---------|-----------------|-------------|-------|
| Title text | 4.50", 0.44" | 4.50", 0.79" | NT Bold, `#000000` |
| Slide number | Bottom-right | — | — |
| NT Logo | Bottom-left | — | `image2.png` |
| Copyright | Bottom-right | — | — |
| Yellow accent dot | Bottom-right corner | — | Small yellow shape |

**Placeholders**: Body (idx=1), Slide Number (idx=2)
**Content area**: Right half (~4.5" wide starting from x≈4.5")

---

## Layout 3: 2_Custom Layout (Image Left + Text Right)

**Background**: White
**Purpose**: Two-column layout — image/picture on left, text blocks on right
**Visual**: Yellow accent pill on far left, picture placeholder center-left, two text blocks stacked on right

| Element | Position (x, y) | Size (w, h) | Notes |
|---------|-----------------|-------------|-------|
| Title text | 0.66", 0.44" | 4.39", 0.79" | NT Bold, `#000000` |
| Picture placeholder | 0.70", 1.81" | 5.74", 4.80" | For image content |
| Text block 1 (top) | 8.00", 2.29" | 4.00", 1.41" | NT Regular body text |
| Text block 2 (bottom) | 8.00", 4.46" | 3.99", 1.41" | NT Regular body text |
| Yellow accent shapes | Left edge + center-right | — | Decorative pills |

**Placeholders**: Body (idx=1), Body (idx=21), Body (idx=22), Picture (idx=23), Slide Number (idx=2)

---

## Layout 4: 3_Custom Layout (Content + Right Image)

**Background**: White
**Purpose**: Text content on left, large circular/rounded cityscape image on right
**Visual**: Text area left side, large yellow-tinted cityscape in rounded shape on right

| Element | Position (x, y) | Size (w, h) | Notes |
|---------|-----------------|-------------|-------|
| Title text | 0.66", 0.44" | 4.38", 0.79" | NT Bold, `#000000` |
| Body text | 0.66", 1.61" | 4.69", 4.47" | NT Regular, `#000000` |
| Decorative image | Right half | — | Large cityscape in rounded shape |

**Placeholders**: Body (idx=1) for title, Body (idx=21) for content, Slide Number (idx=2)

---

## Layout 5: 4_Custom Layout (Empty/Flexible)

**Background**: White
**Purpose**: Minimal layout for flexible content — charts, diagrams, freeform
**Visual**: Yellow accent pill shapes decorating edges, large open content area

**Placeholders**: Slide Number (idx=2) only — no text placeholders, fully manual content placement

---

## Layout 6: 5_Custom Layout (Multi-image Showcase)

**Background**: White
**Purpose**: Showcase with 4 tall pill-shaped image containers + text
**Visual**: Title on left, then 4 tall rounded pill shapes in a row with progressive fill (gray → yellow)

| Element | Position (x, y) | Size (w, h) | Notes |
|---------|-----------------|-------------|-------|
| Title text | 0.66", 0.44" | 4.42", 0.79" | NT Bold, `#000000` |
| Subtitle text | 0.66", 1.63" | 4.67", 4.46" | NT Regular |
| 4 pill shapes | Right side | ~2.5"w each | Tall rounded rectangles with images |

**Placeholders**: Body (idx=1), Body (idx=21), Slide Number (idx=2)

---

## Layout 7: 6_Custom Layout (Four-Column Cards)

**Background**: White
**Purpose**: Four equal-width pill-shaped cards in a row, each with a header and description
**Visual**: Title top area, 4 yellow pill columns below with text inside

| Element | Position (x, y) | Size (w, h) | Notes |
|---------|-----------------|-------------|-------|
| Title text | 4.50", 0.44" | 4.56", 0.79" | NT Bold, `#000000` |
| Subtitle | 0.70", 1.48" | 11.95", 1.21" | NT Regular for description |
| Card 1 header | 0.77", 4.41" | 1.38", 0.42" | NT Bold in pill |
| Card 1 body | 0.72", 5.07" | 1.49", 0.71" | NT Regular in pill |
| Card 2 header | 4.24", 4.41" | 1.38", 0.42" | NT Bold in pill |
| Card 2 body | 4.19", 5.07" | 1.49", 0.71" | NT Regular in pill |
| Card 3 header | 7.72", 4.41" | 1.38", 0.42" | NT Bold in pill |
| Card 3 body | 7.67", 5.07" | 1.48", 0.71" | NT Regular in pill |
| Card 4 header | 11.15", 4.41" | 1.47", 0.44" | NT Bold in pill |
| Card 4 body | 11.15", 5.07" | 1.48", 0.67" | NT Regular in pill |

**Placeholders**: Body (idx=1), plus idx=21–29 for card headers and bodies, Slide Number (idx=2)

---

## Layout 8: 7_Custom Layout (Minimal with Accent Bar)

**Background**: White
**Purpose**: Clean minimal layout with a small yellow accent bar in the top-left corner
**Visual**: Single yellow vertical bar top-left, large open space for content

| Element | Position (x, y) | Size (w, h) | Notes |
|---------|-----------------|-------------|-------|
| Title text | 0.39", 0.29" | 4.33", 0.79" | NT Bold, `#000000` |
| Yellow accent bar | Top-left | — | Small vertical yellow rectangle |

**Placeholders**: Body (idx=1), Slide Number (idx=2)

---

## Layout 9: 9_Custom Layout (Yellow BG with White Header)

**Background**: Solid yellow `#FFD100`
**Purpose**: Yellow section slide with white header banner area at top
**Visual**: White rounded-corner banner at top (for title), yellow body below

| Element | Position (x, y) | Size (w, h) | Notes |
|---------|-----------------|-------------|-------|
| Title text | 0.39", 0.29" | 4.33", 0.79" | NT Bold in white banner area |
| Body text | 0.66", 1.63" | 12.07", 5.01" | NT Regular, `#000000` on yellow |
| White header band | Top | Full width | Rounded bottom-right corner |

**Placeholders**: Body (idx=1), Body (idx=21), Slide Number (idx=2)

---

## Layout 10: 10_Custom Layout (White Header + Yellow Body)

**Background**: White top + Yellow body
**Purpose**: Content slide with white header zone and yellow main area
**Visual**: Thin black top line, white header band with rounded pill shape, yellow body

| Element | Position (x, y) | Size (w, h) | Notes |
|---------|-----------------|-------------|-------|
| Title text | 0.39", 0.29" | 4.33", 0.79" | NT Bold in white header |
| Body text | 0.66", 1.63" | 12.07", 5.01" | NT Regular, `#000000` on yellow |

**Placeholders**: Body (idx=1), Body (idx=21), Slide Number (idx=2)

---

## Layout 11: 8_Custom Layout (Closing Slide)

**Background**: Yellow `#FFD100` with cityscape background image
**Purpose**: Final/closing slide with company information
**Visual**: Full cityscape image with yellow overlay, white pill shape center with NT logo and company text

Fixed content (embedded in layout):
- NT logo (large, in white pill area)
- Company name: บริษัท โทรคมนาคมแห่งชาติ จำกัด (มหาชน)
- English name: National Telecom Public Company Limited
- Yellow separator line
- Website: www.ntplc.co.th | Contact Center 1888

**Placeholders**: Slide Number (idx=2) only — all content is pre-built into the layout

---

## Common Footer Positioning

For all content slides (not title or closing):

| Element | Position | Alignment |
|---------|----------|-----------|
| NT Logo | x≈0.15", y≈6.85" | Bottom-left |
| Copyright text | x≈9.5", y≈7.05" | Bottom-right |
| Slide number | Near copyright | Bottom-right |

---

## Content Area Safe Zones

When creating slides from scratch, keep content within these bounds:

| Slide Type | Content Area |
|------------|-------------|
| Full-width content | x: 0.5"–12.8", y: 0.3"–6.7" |
| Left-column (with right decoration) | x: 0.5"–5.5", y: 0.3"–6.7" |
| Right-column (with left decoration) | x: 4.5"–12.8", y: 0.3"–6.7" |
| Title area | x: 0.4"–5.0", y: 0.3"–1.2" |
| Footer reserved zone | y: 6.8"–7.5" (do not place content here) |
