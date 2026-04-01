# Tokens — Tetris Library 2.0

> Semantic guide for AI component composition. Values live in `tokens.css`.
> **Rule:** Use Alias Tokens in components. Core Tokens = raw primitives, never apply directly.
> **Chain:** Component → Alias Token → Core Token → CSS value

---

## Alias Tokens

### Color

**Background**  [css: background-color]
```
color-background-primary    →  white-alpha/100               ·  page, card, modal — light surface
color-background-secondary  →  gray/100                      ·  secondary page bg — improves legibility behind white-block layouts
color-background-inverse    →  gray/900                      ·  dark/inverted surface
color-background-overlay    →  black-alpha/70                ·  scrim — drawer, dialog, modal
```

**Border**  [css: border-color]
```
color-border-primary   →  gray/300                      ·  static cards, containers, dividers — idle
color-border-disabled  →  gray/200                      ·  any disabled element border
color-border-inverse   →  white-alpha/100               ·  border/divider on dark surface
```

**Brand**  [css: background-color / color / fill]
```
color-brand-fill          →  yellow/500                    ·  brand-yellow fill — CTA, promo
color-brand-text-on-fill  →  gray/900                      ·  text on brand-yellow bg
color-brand-icon-on-fill  →  gray/900                      ·  icon on brand-yellow bg
```

**Fill**  [css: background-color]
```
color-fill-disabled  →  gray/200                      ·  bg fill on any disabled element
```

**Icon**  [css: fill / color]
```
color-icon-primary           →  gray/800                      ·  icon on light surface, no interaction
color-icon-disabled          →  gray/300                      ·  icon — disabled state
color-icon-disabled-on-fill  →  gray/500                      ·  icon — disabled, on filled bg
color-icon-inverse           →  white-alpha/100               ·  icon on dark surface
```

**Surface**  [css: background-color]
```
color-surface-primary    →  white-alpha/100               ·  card, modal, container — primary level
color-surface-secondary  →  gray/100                      ·  nested container, list row
color-surface-tertiary   →  gray/200                      ·  deeply nested, disabled input bg
color-surface-hover      →  black-alpha/10                ·  hover overlay on row/surface
color-surface-active     →  black-alpha/20                ·  press overlay on row/surface
```

**Text**  [css: color]
```
color-text-primary      →  gray/900                      ·  headings, body, high-emphasis labels
color-text-secondary    →  gray/600                      ·  subtitles, supporting copy
color-text-tertiary     →  gray/500                      ·  captions, hints, low-emphasis
color-text-disabled     →  gray/400                      ·  text on disabled elements
color-text-inverse      →  white-alpha/100               ·  text on dark surface
color-text-placeholder  →  gray/500                      ·  input placeholder
```

**Interactive — Border**  [css: border-color]
```
color-interactive-border-default  →  gray/300                      ·  input/control border — idle
color-interactive-border-hover    →  gray/400                      ·  input/control border — hover
color-interactive-border-active   →  blue/700                      ·  input/control border — focused
```

**Interactive — Fill (loud)**  [css: background-color]
```
color-interactive-fill-loud-default  →  blue/700                      ·  primary button — idle
color-interactive-fill-loud-hover    →  blue/800                      ·  primary button — hover
color-interactive-fill-loud-active   →  blue/900                      ·  primary button — pressed
```

**Interactive — Fill (quiet)**  [css: background-color]
```
color-interactive-fill-quiet-default  →  blue/100                      ·  secondary button — idle
color-interactive-fill-quiet-hover    →  blue/200                      ·  secondary button — hover
color-interactive-fill-quiet-active   →  blue/300                      ·  secondary button — pressed
```

**Interactive — Fill (quiet-inverse)**  [css: background-color]
```
color-interactive-fill-quiet-inverse-default   →  gray/700                      ·  secondary btn on dark — idle
color-interactive-fill-quiet-inverse-hover     →  gray/600                      ·  secondary btn on dark — hover
color-interactive-fill-quiet-inverse-disabled  →  gray/800                      ·  secondary btn on dark — disabled
```

**Interactive — Fill (mute/ghost)**  [css: background-color]
```
color-interactive-fill-mute-default  →  transparent                   ·  ghost button — idle (transparent)
color-interactive-fill-mute-hover    →  blue/100                      ·  ghost button — hover
color-interactive-fill-mute-active   →  blue/200                      ·  ghost button — pressed
```

**Interactive — Icon**  [css: fill / color]
```
color-interactive-icon-default          →  gray/900                      ·  clickable icon — idle
color-interactive-icon-hover            →  gray/800                      ·  clickable icon — hover
color-interactive-icon-active           →  gray/700                      ·  clickable icon — pressed
color-interactive-icon-default-accent   →  blue/700                      ·  clickable icon accent — idle
color-interactive-icon-hover-accent     →  blue/800                      ·  clickable icon accent — hover
color-interactive-icon-active-accent    →  blue/900                      ·  clickable icon accent — pressed
color-interactive-icon-default-inverse  →  white-alpha/100               ·  clickable icon on dark — idle
```

**Interactive — Text**  [css: color]
```
color-interactive-text-default  →  blue/700                      ·  link/action text — idle
color-interactive-text-hover    →  blue/800                      ·  link/action text — hover
color-interactive-text-active   →  blue/900                      ·  link/action text — pressed
```

**Selected**  [css: border-color]
```
color-selected-border-default  →  blue/700                      ·  selected/checked border — idle
color-selected-border-hover    →  blue/800                      ·  selected border — hover
color-selected-border-active   →  blue/900                      ·  selected border — pressed
```

**Feedback — Border**  [css: border-color]
```
color-feedback-border-positive-loud     →  green/500                     ·  positive feedback border
color-feedback-border-negative-loud     →  red/500                       ·  error feedback border
color-feedback-border-caution-loud      →  orange/500                    ·  warning feedback border
color-feedback-border-informative-loud  →  gray/700                      ·  informative feedback border
```

**Feedback — Fill**  [css: background-color]
```
color-feedback-fill-positive-loud      →  green/500                     ·  positive badge/alert — loud
color-feedback-fill-positive-quiet     →  green/100                     ·  positive badge/alert — quiet
color-feedback-fill-negative-loud      →  red/500                       ·  error badge/alert — loud
color-feedback-fill-negative-quiet     →  red/100                       ·  error badge/alert — quiet
color-feedback-fill-caution-loud       →  orange/500                    ·  warning badge/alert — loud
color-feedback-fill-caution-quiet      →  orange/100                    ·  warning badge/alert — quiet
color-feedback-fill-informative-loud   →  gray/700                      ·  info badge/alert — loud
color-feedback-fill-informative-quiet  →  gray/200                      ·  info badge/alert — quiet
```

**Feedback — Text**  [css: color]
```
color-feedback-text-positive-loud      →  green/900                     ·  positive text — max contrast
color-feedback-text-positive-quiet     →  green/500                     ·  positive text — standard contrast
color-feedback-text-negative-loud      →  red/900                       ·  error text — max contrast
color-feedback-text-negative-quiet     →  red/500                       ·  error text — standard contrast
color-feedback-text-caution-loud       →  orange/900                    ·  warning text — max contrast
color-feedback-text-caution-quiet      →  orange/500                    ·  warning text — standard contrast
color-feedback-text-informative-loud   →  gray/900                      ·  info text — max contrast
color-feedback-text-informative-quiet  →  gray/700                      ·  info text — standard contrast
```

**Feedback — Icon**  [css: fill / color]
```
color-feedback-icon-positive-loud      →  green/900                     ·  positive icon — max contrast
color-feedback-icon-positive-quiet     →  green/500                     ·  positive icon — standard
color-feedback-icon-negative-loud      →  red/900                       ·  error icon — max contrast
color-feedback-icon-negative-quiet     →  red/500                       ·  error icon — standard
color-feedback-icon-caution-loud       →  orange/900                    ·  warning icon — max contrast
color-feedback-icon-caution-quiet      →  orange/500                    ·  warning icon — standard
color-feedback-icon-informative-loud   →  gray/900                      ·  info icon — max contrast
color-feedback-icon-informative-quiet  →  gray/700                      ·  info icon — standard
```

### Spacing

**Gap**  [css: gap]
```
spacing-gap-none  →  spacing/none                  ·  0 gap
spacing-gap-2xs   →  spacing/7xs                   ·  4px — badge icon+label
spacing-gap-xs    →  spacing/6xs                   ·  8px — compact inline
spacing-gap-s     →  spacing/4xs                   ·  16px — standard inline
spacing-gap-m     →  spacing/2xs                   ·  24px — content block
spacing-gap-l     →  spacing/xs                    ·  32px — section gap
spacing-gap-xl    →  spacing/s                     ·  40px — large layout
spacing-gap-2xl   →  spacing/m                     ·  48px — extra-large layout
```

**Padding**  [css: padding]
```
spacing-padding-none  →  spacing/none                  ·  0 padding
spacing-padding-3xs   →  spacing/4xs                   ·  16px — badge, button-sm
spacing-padding-2xs   →  spacing/3xs                   ·  20px — small component
spacing-padding-xs    →  spacing/2xs                   ·  24px — input, list item
spacing-padding-s     →  spacing/xs                    ·  32px — card, panel
spacing-padding-m     →  spacing/s                     ·  40px — medium container
spacing-padding-l     →  spacing/m                     ·  48px — large container
spacing-padding-xl    →  spacing/xl                    ·  64px — page horizontal
spacing-padding-2xl   →  spacing/2xl                   ·  80px — large section
```

---

## Decision Guide

> Extracted from Figma Tetris DS foundation pages.
> Use these rules when choosing between tokens during component composition.

---

### 1. Layering — Level Rules

```
Lv1  Background  → color-background-*
Lv2  Surface     → color-surface-*
Lv3  Component   → built component placed on top

Valid stacking:
  Lv1 → Lv2 → Lv3  ✓
  Lv1 → Lv3        ✓  (skip surface)
  Lv1 → Lv2        ✓  (no component on top)

Invalid:
  Lv2 → Lv1        ✗
  Lv3 → Lv1        ✗
  any level going back down  ✗
```

---

### 2. Background vs Surface

```
BACKGROUND = full-screen/page layer (behind everything)
SURFACE    = container/component layer (cards, panels, rows)

screen/page bg                    → color-background-primary
  └─ ideal pair for cards on it   → color-surface-primary (NOT color-background-primary again)

secondary bg (improves legibility
  behind white-block layouts)     → color-background-secondary
  └─ ideal pair for cards on it   → color-surface-secondary

dark/inverted screen (robotics,
  not dark mode)                  → color-background-inverse
  └─ text on it                   → color-text-inverse
  └─ icons on it                  → color-icon-inverse
  └─ borders on it                → color-border-inverse

scrim behind drawer/dialog/modal  → color-background-overlay

surface-primary on primary-bg     ✗ avoid — same visual level, no hierarchy
surface-secondary on primary-bg   ✓ correct — creates depth
surface-tertiary after secondary  ✓ correct — e.g., tables inside cards
```

---

### 3. Surface — Static vs Interactive

```
Static surface (cards, panels)    → color-surface-primary / secondary / tertiary
Interactive surface (tappable row,
  hoverable card):
  hover state overlay             → color-surface-hover  (apply ON TOP of surface bg)
  pressed state overlay           → color-surface-active (apply ON TOP of surface bg)

Note: surface-hover/active are overlays, not replacements for the base surface color.
```

---

### 4. Border — Which token?

```
Static containers (cards, blocks,
  non-interactive)                → color-border-primary
Input/control — idle              → color-interactive-border-default
Input/control — hover             → color-interactive-border-hover
Input/control — focused/active    → color-interactive-border-active
Checkbox/radio — selected         → color-selected-border-default
Checkbox/radio — selected hover   → color-selected-border-hover
Disabled element                  → color-border-disabled
On background-inverse surface     → color-border-inverse (static only)
Feedback component border         → color-feedback-border-[type]-loud
```

---

### 5. Interactive Action Tiers

```
LOUD   = primary action   → color-interactive-fill-loud-[state]
  pair with: color-text-inverse + color-icon-inverse

QUIET  = secondary action → color-interactive-fill-quiet-[state]
  pair with: color-interactive-text-default + color-interactive-icon-default-accent

MUTE   = tertiary/ghost   → color-interactive-fill-mute-[state]
  pair with: color-interactive-text-default + color-interactive-icon-default-accent

QUIET-INVERSE = secondary on dark bg → color-interactive-fill-quiet-inverse-[state]
  pair with: color-text-inverse + color-icon-inverse

State chain (all tiers):
  idle     → -default
  hover    → -hover
  pressed  → -active
  disabled → color-fill-disabled (bg) + color-border-disabled + color-text-disabled + color-icon-disabled
```

---

### 6. Icons

```
Static icon, light surface        → color-icon-primary
Static icon, dark/inverse surface → color-icon-inverse
Clickable icon (no accent)        → color-interactive-icon-default
Clickable icon (accent/blue)      → color-interactive-icon-default-accent
Icon on brand-yellow fill         → color-brand-icon-on-fill
Disabled icon (light bg)          → color-icon-disabled
Disabled icon (on filled bg)      → color-icon-disabled-on-fill
  ↑ rule: when fill = color-fill-disabled → icon must be color-icon-disabled-on-fill

Clickable icon state chain:
  idle    → color-interactive-icon-default / -accent / -inverse
  hover   → color-interactive-icon-hover / -hover-accent
  pressed → color-interactive-icon-active / -active-accent
```

---

### 7. Text Hierarchy

```
High emphasis (headings, display)  → color-text-primary
Medium (body, labels)              → color-text-secondary
Low (captions, hints)              → color-text-tertiary
Disabled element                   → color-text-disabled
On dark/inverse surface            → color-text-inverse
Input before interaction           → color-text-placeholder
On brand-yellow fill               → color-brand-text-on-fill
Interactive/link text              → color-interactive-text-default / -hover / -active
```

---

### 8. Feedback — Loud vs Quiet + Pairing Rules

```
LOUD  = high-contrast solid fill → standalone badges, snackbars, toasts
QUIET = low-contrast tinted fill → inline banners, form hints, subtle indicators

Required pairings (never mix loud/quiet between fill and text/icon):

Positive:
  fill-positive-loud  + text-inverse         ✓
  fill-positive-loud  + icon-inverse         ✓
  fill-positive-quiet + text-positive-loud   ✓
  fill-positive-quiet + icon-positive-loud   ✓

Caution:
  fill-caution-loud   + text-inverse         ✓
  fill-caution-loud   + icon-inverse         ✓
  fill-caution-quiet  + text-caution-loud    ✓
  fill-caution-quiet  + icon-caution-loud    ✓

Negative:
  fill-negative-loud  + text-inverse         ✓
  fill-negative-loud  + icon-inverse         ✓
  fill-negative-quiet + text-negative-loud   ✓
  fill-negative-quiet + icon-negative-loud   ✓

Feedback borders:
  with fill-[type]-quiet → add color-feedback-border-[type]-loud
  without fill           → color-feedback-border-[type]-loud alone is valid
```

---

### 9. Spacing — Gap vs Padding

```
GAP     = space BETWEEN sibling elements (flex/grid gap)
          → use spacing-gap-* tokens

PADDING = space INSIDE a container (internal inset)
          → use spacing-padding-* tokens

Scale reference:
  2xs  4px  → tight pairs (badge icon+label, chip icon+text)
  xs   8px  → compact inline elements
  s    16px → standard inline gap / compact padding
  m    24px → content block gap / standard component padding
  l    32px → section gap / standard container padding
  xl   40px → large layout gap
  2xl  48px → extra-large layout / page sections

Rule: never use raw spacing/* Core Tokens directly.
      always go through spacing-gap-* or spacing-padding-* Alias Tokens.
```

---

### 10. Secondary Colors (data viz only)

```
Secondary palette (olive, pink, teal, violet, yellow, etc.) is for:
  → data visualization charts, graphs, complex visualizations
  → NOT for UI components or interactive elements

Rules when using for charts:
  - alternate light/dark values for category differentiation
  - use patterns/textures when colors repeat or for colorblind users
  - use tonal contrast (not just hue) between adjacent series
  - tone-100 only to highlight selected/clicked elements
```

---

### 11. Border Width

```
1px (border-width-s)  → static / non-interactive elements (cards, dividers, containers)
2px (border-width-m)  → interactive default state (inputs, selects, checkboxes)
3px (border-width-l)  → interactive hover / pressed state
4px (border-width-xl) → user-chosen context borders (decorative, highlight, callout)
```

---

### 12. Border Radius

```
Proportional rule: applies only when no radius is explicitly specified.
If Figma or the designer proposes a value → that value takes precedence.

Element ≤ 72px  → border-radius-s  (12px)
  badge, chip, tag, icon button, toggle, small input

Element > 72px  → border-radius-m  (16px)
  card, input, button-lg, modal, drawer, panel

Special cases:
  pill / circular  → border-radius-circle (9999)
  no radius needed → border-radius-none   (0)

Rule: never mix different radii within the same component layer.
```

---

### 13. Motion — When to use each duration

```
Principle: Simple, Efficient, Explicit.
Operational UI must stay in 100–300ms. Never use 500ms+ on interactive controls.

FAST (100ms — XS)
  → hover state changes, microinteractions, button feedback, radio/checkbox, cell/card selection

DEFAULT (200–300ms — S / M)
  → standard transitions: menus, drawers, bottom sheets, modals, dropdowns, toasts, page transitions

SLOW (500–800ms — L / XL)
  → page-level overlays, complex state changes, entrance of large surfaces

STORYTELLER (1200–2400ms — 2XL / 3XL)
  → toast timeout animations, illustration animations, onboarding sequences

Easing:
  ease-in   cubic-bezier(0.4, 0, 1, 1)   → element entering the screen
  ease-out  cubic-bezier(0, 0, 0.2, 1)   → element leaving the screen

Delay:
  none    0ms   → immediate — default for most interactions
  short   100ms → quick feedback after a trigger
  medium  200ms → staggered elements in a list
  long    300ms → sequential step-by-step transitions
```

---

## Core Tokens

> Raw primitives. Referenced by Alias Tokens — never use directly in components.

### Color Palette

**Base**
```
color-transparent  rgba(255,255,255,0)
```

**Gray**
```
color-gray-100  #EDEDF7
color-gray-200  #DEDFED
color-gray-300  #BDBFD6
color-gray-400  #9CA0BF
color-gray-500  #737396
color-gray-600  #5A5A7C
color-gray-700  #454768
color-gray-800  #2F2F46
color-gray-900  #1C1C2B
```

**Blue**
```
color-blue-100  #E0E9FF
color-blue-200  #CCDAFF
color-blue-300  #B8C8FF
color-blue-400  #A3B9FF
color-blue-500  #8AA0FF
color-blue-600  #6F80FB
color-blue-700  #4850E5
color-blue-800  #353AC5
color-blue-900  #272C96
```

**Green**
```
color-green-100  #DBF0E2
color-green-200  #DBF0E2
color-green-300  #DBF0E2
color-green-400  #DBF0E2
color-green-500  #068943
color-green-600  #067A3B
color-green-700  #067A3B
color-green-800  #034E26
color-green-900  #034E26
```

**Red**
```
color-red-100  #FEE2EA
color-red-200  #FEE2EA
color-red-300  #FEE2EA
color-red-400  #FEE2EA
color-red-500  #DA0B38
color-red-600  #C20A32
color-red-700  #C20A32
color-red-800  #7E0620
color-red-900  #7E0620
```

**Orange**
```
color-orange-100  #FCE2D4
color-orange-200  #FCE2D4
color-orange-300  #FCE2D4
color-orange-400  #FCE2D4
color-orange-500  #EC5809
color-orange-600  #CB4E0B
color-orange-700  #CE4D09
color-orange-800  #993906
color-orange-900  #993906
```

**Yellow**
```
color-yellow-100  #F6F0BE
color-yellow-200  #F6F0BE
color-yellow-300  #F6F0BE
color-yellow-400  #F6F0BE
color-yellow-500  #FFE600
color-yellow-600  #F6B900
color-yellow-700  #F6B900
color-yellow-800  #623502
color-yellow-900  #623502
```

**Pink**
```
color-pink-100  #FAE5F3
color-pink-200  #FAE5F3
color-pink-300  #EB76B2
color-pink-400  #EB76B2
color-pink-500  #DF0E77
color-pink-600  #B3035B
color-pink-700  #B3035B
color-pink-800  #820443
color-pink-900  #820443
```

**Teal**
```
color-teal-100  #DAEDF1
color-teal-200  #DAEDF1
color-teal-300  #6DB7C6
color-teal-400  #6DB7C6
color-teal-500  #00819B
color-teal-600  #006B80
color-teal-700  #006B80
color-teal-800  #004A58
color-teal-900  #004A58
```

**Olive**
```
color-olive-100  #ECF0D1
color-olive-200  #ECF0D1
color-olive-300  #ADB66B
color-olive-400  #ADB66B
color-olive-500  #717D05
color-olive-600  #515F03
color-olive-700  #515F03
color-olive-800  #3B4211
color-olive-900  #3B4211
```

**Violet**
```
color-violet-100  #E9DDFD
color-violet-200  #E9DDFD
color-violet-300  #BD8FFE
color-violet-400  #BD8FFE
color-violet-500  #9141FF
color-violet-600  #6E1CE3
color-violet-700  #6E1CE3
color-violet-800  #46297A
color-violet-900  #46297A
```

**Black Alpha**
```
color-black-alpha-10   rgba(47,47,70,0.1)
color-black-alpha-20   rgba(47,47,70,0.15)
color-black-alpha-30   rgba(47,47,70,0.3)
color-black-alpha-40   rgba(47,47,70,0.4)
color-black-alpha-50   rgba(47,47,70,0.5)
color-black-alpha-60   rgba(47,47,70,0.6)
color-black-alpha-70   rgba(47,47,70,0.7)
color-black-alpha-80   rgba(47,47,70,0.8)
color-black-alpha-90   rgba(47,47,70,0.9)
color-black-alpha-100  #2F2F46
```

**White Alpha**
```
color-white-alpha-10   rgba(255,255,255,0.1)
color-white-alpha-20   rgba(255,255,255,0.2)
color-white-alpha-30   rgba(255,255,255,0.3)
color-white-alpha-40   rgba(255,255,255,0.4)
color-white-alpha-50   rgba(255,255,255,0.5)
color-white-alpha-60   rgba(255,255,255,0.6)
color-white-alpha-70   rgba(255,255,255,0.7)
color-white-alpha-80   rgba(255,255,255,0.8)
color-white-alpha-90   rgba(255,255,255,0.9)
color-white-alpha-100  #FFFFFF
```

### Typography

**Font Family**
```
font-family-default  Inter
```

**Font Size**
```
font-size-100   16
font-size-200   20
font-size-300   24
font-size-400   28
font-size-500   32
font-size-600   40
font-size-700   48
font-size-800   64
font-size-900   88
font-size-1000  128
font-size-1100  160
font-size-1200  200
font-size-1300  240
```

**Line Height**
```
font-line-height-100   16
font-line-height-200   20
font-line-height-300   24
font-line-height-400   28
font-line-height-450   32
font-line-height-500   36
font-line-height-550   40
font-line-height-600   48
font-line-height-700   56
font-line-height-800   72
font-line-height-900   92
font-line-height-1000  128
font-line-height-1100  160
font-line-height-1200  192
font-line-height-1300  220
```

**Font Weight**
```
font-weight-light     light
font-weight-regular   Regular
font-weight-medium    Medium
font-weight-semibold  Semibold
```

### Spacing

**Scale**
```
spacing-none  0
spacing-7xs   4
spacing-6xs   8
spacing-5xs   12
spacing-4xs   16
spacing-3xs   20
spacing-2xs   24
spacing-xs    32
spacing-s     40
spacing-m     48
spacing-l     56
spacing-xl    64
spacing-2xl   80
spacing-3xl   104
spacing-4xl   128
spacing-5xl   160
spacing-6xl   200
```

### Border

**Border Radius**
```
border-radius-none    0
border-radius-2xs     4
border-radius-xs      8
border-radius-s       12
border-radius-m       16
border-radius-l       24
border-radius-xl      32
border-radius-2xl     40
border-radius-circle  9999
```

**Border Width**
```
border-width-none  0
border-width-s     1
border-width-m     2
border-width-l     3
border-width-xl    4
```

### Motion

**Duration**  [note: scale uses uppercase — XS S M L XL 2XL 3XL]
```
motion-duration-XS   100ms
motion-duration-S    200ms
motion-duration-M    300ms
motion-duration-L    500ms
motion-duration-XL   800ms
motion-duration-2XL  1200ms
motion-duration-3XL  2400ms
```

**Easing**
```
motion-easing-ease-in   cubic-bezier(0.4, 0, 1, 1)
motion-easing-ease-out  cubic-bezier(0, 0, 0.2, 1)
```

**Delay**
```
motion-delay-none    0ms
motion-delay-short   100ms
motion-delay-medium  200ms
motion-delay-long    300ms
```