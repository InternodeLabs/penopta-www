# Penopta Web App — Design System

**Product:** Penopta  
**Surface:** Web application (not marketing / landing page)  
**Source:** Derived from the Penopta landing page visual language (Gradient Labs–inspired), adapted for daily product use.

---

## Purpose

This document defines how to style the Penopta **web app**. It preserves the same brand feel as the landing page — warm cream backgrounds, orange accent, Inter typography, soft borders — but shifts the system toward **density, clarity, and function**.

### Landing page → web app changes

| Landing page | Web app |
|---|---|
| Large display headlines | Compact page titles |
| Hero mockups & illustration placeholders | No illustrations; UI chrome only |
| Centered marketing sections | Sidebar + main content layout |
| Decorative vertical grid on body | Plain cream background (no grid texture) |
| Generous marketing spacing | Tighter, consistent spacing scale |
| Serif italic accents in footer | Sans-serif only in product UI |

---

## Design principles

1. **Content over decoration** — No hero images, feature illustrations, or gradient placeholder panels.
2. **Smaller type, tighter rhythm** — Optimize for scanning and working, not selling.
3. **Surfaces, not sections** — Use white panels on cream canvas; avoid stacked marketing blocks.
4. **One accent color** — Orange for primary actions and eyebrow labels only; black for secondary emphasis.
5. **Plain language UI** — Short labels, no marketing copy patterns inside the app.

---

## Color tokens

Use these CSS custom properties everywhere. Do not introduce new hues without a design reason.

```css
--white:        #ffffff;   /* panels, inputs, dropdowns */
--cream:        #faf7f0;   /* app canvas / page background */
--cream-light:  #fdfbf7;   /* subtle hover on canvas (optional) */
--border:       #ede9de;   /* dividers, card borders, input outlines */
--muted:        #67675f;   /* secondary text, placeholders, meta */
--charcoal:     #383835;   /* body text alternative (rare) */
--black:        #000000;   /* primary text, nav CTA, icons */
--orange:       #ff8933;   /* primary button, active states, eyebrows */
--orange-light: #ffa666;   /* primary button hover */
--orange-tint:  #fbe8df;   /* subtle highlight bg (badges, selected row) */
```

### Usage rules

- **Canvas:** `--cream` for the full app background.
- **Panels:** `--white` with `1px solid var(--border)`.
- **Primary action:** `--orange` background, `--black` text.
- **Secondary action:** `--white` or transparent with `--border` outline, `--black` text.
- **Destructive:** not defined in brand yet — use `--black` text + border until a red is added.
- **Do not use** `--blue-tint` or illustration gradients in the web app.

---

## Typography

**Font stack:** `"Inter", system-ui, -apple-system, sans-serif`  
**Base size:** `14px` (`0.875rem`) — smaller than the landing page (`16px`).

Enable antialiasing: `-webkit-font-smoothing: antialiased`.

### Type scale (web app)

| Role | Size | Weight | Line height | Letter spacing | Color |
|---|---|---|---|---|---|
| Page title | 20px / 1.25rem | 500 | 1.25 | -0.03em | black |
| Section title | 16px / 1rem | 500 | 1.3 | -0.02em | black |
| Body | 14px / 0.875rem | 400 | 1.55 | -0.015em | black |
| Body secondary | 14px / 0.875rem | 400 | 1.55 | -0.015em | muted |
| Small / meta | 12px / 0.75rem | 400 | 1.5 | -0.01em | muted |
| Eyebrow label | 13px / 0.8125rem | 500 | 1.4 | -0.01em | orange |
| Button | 13px / 0.8125rem | 500 | 1 | -0.01em | black (on orange) |
| Nav link | 12px / 0.75rem | 400–500 | 1.4 | -0.01em | black |

### Landing → app size mapping (reference)

| Landing | Web app |
|---|---|
| Hero h1 ~48px | Page title 20px |
| Section h2 ~40px | Section title 16px |
| Card h3 ~20px | Panel title 14–16px |
| Body ~16–18px | Body 14px |
| Eyebrow ~17px | Eyebrow 13px |

### Copy rules (in-app)

- Page titles: one short phrase, max ~6 words.
- Section titles: label the task area, not a value prop.
- Helper text: one line when possible; max two.
- No italic serif accents in product UI.

---

## Spacing

Use a **4px base grid**. Prefer these tokens:

```css
--space-1:  4px;
--space-2:  8px;
--space-3:  12px;
--space-4:  16px;
--space-5:  20px;
--space-6:  24px;
--space-8:  32px;
--space-10: 40px;
```

| Context | Padding / gap |
|---|---|
| App shell (sidebar item) | 8px 12px |
| Top bar height | 48–56px |
| Panel padding | 16–20px |
| Stack gap (form fields) | 12px |
| Stack gap (sections in page) | 24–32px |
| Page padding (main content) | 24px desktop / 16px mobile |

Avoid landing-page section padding (`3rem–4.5rem`). App pages should feel continuous, not segmented.

---

## Border radius

Smaller radii than marketing cards — UI should feel precise.

```css
--radius-xs:  6px;    /* chips, tags, small controls */
--radius-sm:  8px;    /* inputs, buttons (non-pill), list items */
--radius-md:  12px;   /* panels, modals, dropdowns */
--radius-lg:  16px;   /* large containers (rare) */
--radius-pill: 100px; /* primary & nav pill buttons only */
```

Landing page used up to `32px` on cards — **do not** use `--radius-lg: 32px` in the app except for pill buttons.

---

## Layout

### App shell

```
┌─────────────────────────────────────────────────┐
│ Top bar (logo, project switcher, user)          │
├──────────┬──────────────────────────────────────┤
│ Sidebar  │ Main content                         │
│ (nav)    │ (white panels on cream canvas)       │
│          │                                      │
└──────────┴──────────────────────────────────────┘
```

- **Sidebar width:** 220–260px fixed; collapsible on mobile.
- **Main max-width:** none (full width of content area); constrain inner forms to ~640px when appropriate.
- **No** full-bleed marketing hero blocks inside the app.

### Two-column content (settings / detail views)

When mirroring the landing “label + content” pattern (e.g. Problem & solution):

- Left column: eyebrow or section label (~25%), orange, top-aligned.
- Right column: body copy or form (~75%).
- No card background on the row — text sits on cream or inside a single white panel.

---

## Components

### Top navigation bar

- Background: `rgba(250, 247, 240, 0.92)` + `backdrop-filter: blur(12px)`.
- Border: none on bar; optional `1px solid var(--border)` bottom.
- Logo height: **24px** (landing uses 28px).
- Links: 12px, black, no underline.
- **Sign up / primary nav CTA:** black pill, white text, padding `6px 12px`, 12px type.

### Sidebar navigation

- Background: `--cream` (same as canvas) or `--white` with right border.
- Item: 14px, `-0.015em` tracking, padding `8px 12px`, radius `--radius-sm`.
- **Active item:** `--white` background + `1px solid var(--border)` OR `--orange-tint` background.
- **No icons required** unless functional — prefer text labels.

### Eyebrow label

Same style as landing **Problem & solution** label, scaled down:

- Font: Inter 500, **13px**, `--orange`.
- No border, no background, no uppercase.
- Use above page titles or section headers: e.g. `Project settings`, `Connected threads`.

### Buttons

**Primary**

- Background: `--orange` → hover `--orange-light`
- Text: `--black`, 13px, weight 500
- Shape: pill (`border-radius: 100px`)
- Padding: `8px 16px` (landing uses `16px 28px` — smaller in app)

**Secondary**

- Background: `--white`
- Border: `1px solid var(--border)`
- Text: `--black`
- Same size and pill shape as primary, or `--radius-sm` for compact toolbars

**Ghost / text**

- No background; black text; hover `--cream-light` or underline

### Cards & panels

- Background: `--white`
- Border: `1px solid var(--border)`
- Radius: `--radius-md` (12px)
- Padding: `16–20px`
- **No** illustration area at top of cards.

### Lists & tables

- Row padding: `10px 12px`
- Divider: `1px solid var(--border)`
- Hover row: `--cream-light` or `--orange-tint` at 50% opacity
- Header text: 12px, muted, weight 500

### Form inputs

- Height: ~36px
- Font: 14px
- Border: `1px solid var(--border)`; focus: `1px solid var(--black)` or orange ring
- Radius: `--radius-sm` (8px)
- Placeholder: `--muted`
- Label: 13px, weight 500, margin-bottom 6px

### FAQ / accordion pattern (in-app help)

If reused inside app:

- Same as landing FAQ item but denser: padding `12px 16px`, 14px question, 13px answer muted.
- No centered marketing layout — left-aligned, max-width 640px.

### Empty states

- Text only: section title + one line muted body + primary button.
- **No** placeholder boxes, gradients, or grid textures.

---

## Motion

- Transitions: `0.15–0.2s ease` for hover/focus only.
- No scroll animations or marketing reveal effects in the app.

---

## Accessibility

- Minimum touch target: 36×36px.
- Focus visible on all interactive elements (outline or ring).
- Body text contrast: black on cream and on white passes WCAG AA.
- Orange buttons: black text on `#ff8933` — verify contrast for small 13px labels.

---

## CSS starter tokens (web app)

```css
:root {
  /* Colors */
  --white: #ffffff;
  --cream: #faf7f0;
  --cream-light: #fdfbf7;
  --border: #ede9de;
  --muted: #67675f;
  --charcoal: #383835;
  --black: #000000;
  --orange: #ff8933;
  --orange-light: #ffa666;
  --orange-tint: #fbe8df;

  /* Typography */
  --font-sans: "Inter", system-ui, -apple-system, sans-serif;
  --text-xs: 0.75rem;    /* 12px */
  --text-sm: 0.8125rem;  /* 13px */
  --text-base: 0.875rem; /* 14px */
  --text-md: 1rem;       /* 16px */
  --text-lg: 1.25rem;    /* 20px */

  /* Radii */
  --radius-xs: 6px;
  --radius-sm: 8px;
  --radius-md: 12px;
  --radius-lg: 16px;
  --radius-pill: 100px;

  /* Layout */
  --sidebar-width: 240px;
  --topbar-height: 52px;
}
```

---

## Do / don't checklist

**Do**

- White panels on cream background
- Orange pill for the single primary action per view
- Orange eyebrows for section context
- Tight, consistent 14px body type
- Inter with negative letter-spacing on headings

**Don't**

- Hero mockups, illustration slots, or gradient wireframe boxes
- Decorative background grid on the app canvas
- Landing-scale headlines (48px+) inside product screens
- Serif italic marketing accents
- Large marketing section padding between every block

---

## File reference

| Asset | Path |
|---|---|
| Logo | `assets/logo.png` |
| Landing implementation | `index.html`, `styles.css` |
| Landing copy deck | `penopta-design.md` (external) |

This document is the source of truth for **web app** styling. When in doubt, prefer less visual noise and smaller type over matching the landing page literally.
