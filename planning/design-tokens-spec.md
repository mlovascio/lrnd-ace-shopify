# Ace Party & Tent Rental - Design Token Specification

> **Source:** Figma file Mr6M1UwQ0i45tEOMHSHe6G
> **Extracted:** 2026-03-02
> **Status:** AUTHORITATIVE - Use this as the single source of truth for all design values

---

## Color Palette

### Brand Colors

| Token | Hex | Usage |
|-------|-----|-------|
| --primary-blue | #005cba | Nav text, headings, links, logo grid labels, breadcrumbs |
| --secondary-red | #ff595a | Primary button fill, secondary button border, promo bar variant 2 |
| --secondary-yellow | #fcd199 | Promo bar default bg |
| --tertiary-yellow | #fdefdc | Accent backgrounds, card overlays |
| --text-blue | #063666 | Dark blue for body text and headings over light backgrounds |

### Neutral Colors

| Token | Hex | Usage |
|-------|-----|-------|
| --white | #ffffff | Page background, nav bg, button text on dark |
| --black | #000000 | Button text (primary), promo bar text (variant 2) |
| --background-taupe | #fdfcf8 | Logo grid bg, alternating section bg |
| --background-gray | #f0f0f0 | Breadcrumb borders, divider lines |

### Interaction Colors

| Token | Hex | Usage |
|-------|-----|-------|
| --button-hover | #ffaeaf | Primary button hover state, Style4 button border |

### Gradient

| Token | Value | Usage |
|-------|-------|-------|
| --gradient-footer | linear-gradient(to right, #0c6bcd, #387fd7) | Footer background |

### CSS Custom Properties

```css
:root {
  /* Brand */
  --primary-blue: #005cba;
  --secondary-red: #ff595a;
  --secondary-yellow: #fcd199;
  --tertiary-yellow: #fdefdc;
  --text-blue: #063666;

  /* Neutrals */
  --white: #ffffff;
  --black: #000000;
  --background-taupe: #fdfcf8;
  --background-gray: #f0f0f0;

  /* Interaction */
  --button-hover: #ffaeaf;

  /* Gradient */
  --gradient-footer: linear-gradient(to right, #0c6bcd, #387fd7);
}
```

---

## Typography

### Font Families

| Font | Weight | Style | Usage |
|------|--------|-------|-------|
| Geoform | Medium (500) | Uppercase | Headings, navigation, buttons, CTAs, labels |
| Zodiak | Regular (400) | Sentence case | Body text, paragraphs, breadcrumbs, footer copy |

Both are custom fonts. Source and licensing TBD (not from Typekit/Adobe Fonts like the current site's Agenda font). Geoform and Zodiak are the NEW brand fonts from the redesign.

**Fallback stack:** `sans-serif` for Geoform, `serif` for Zodiak (pending confirmation of web font source).

### Typography Scale

Named styles extracted from Figma, organized by size.

#### Display Styles (Geoform Medium, uppercase)

| Style Name | Size | Line Height | Letter Spacing | Tracking (em) |
|------------|------|-------------|----------------|---------------|
| Desktop/.displaySuper | 100px | 100% (100px) | 4% | 0.04em |
| (unnamed - in code) | 70px | 100% | 4% | 0.04em |
| Desktop/.display 1 | 50px | 100% (50px) | 4% | 0.04em |

#### UI Styles (Geoform Medium, uppercase)

| Style Name | Size | Line Height | Letter Spacing | Tracking (em) |
|------------|------|-------------|----------------|---------------|
| All Device/.display 3 | 14px | 1.5 (21px) | 6% | 0.06em |
| All Device/CTA | 12px | 100% (12px) | 4% | 0.04em |
| (unnamed - fine print) | 9px | normal | 6% | 0.06em |

#### Body Styles (Zodiak Regular, sentence case)

| Style Name | Size | Line Height | Letter Spacing |
|------------|------|-------------|----------------|
| All Device/Paragraph | 15px | 1.5 (22.5px) | 0 |
| All Device/Paragraph Small | 12px | 1.5 (18px) | 0 |

### Typography CSS

```css
/* Display - Geoform */
.display-super {
  font-family: 'Geoform', sans-serif;
  font-weight: 500;
  font-size: 100px;
  line-height: 1;
  letter-spacing: 0.04em;
  text-transform: uppercase;
}

.display-1 {
  font-family: 'Geoform', sans-serif;
  font-weight: 500;
  font-size: 50px;
  line-height: 1;
  letter-spacing: 0.04em;
  text-transform: uppercase;
}

.display-3 {
  font-family: 'Geoform', sans-serif;
  font-weight: 500;
  font-size: 14px;
  line-height: 1.5;
  letter-spacing: 0.06em;
  text-transform: uppercase;
}

.cta-text {
  font-family: 'Geoform', sans-serif;
  font-weight: 500;
  font-size: 12px;
  line-height: 1;
  letter-spacing: 0.04em;
  text-transform: uppercase;
}

/* Body - Zodiak */
.paragraph {
  font-family: 'Zodiak', serif;
  font-weight: 400;
  font-size: 15px;
  line-height: 1.5;
  letter-spacing: 0;
}

.paragraph-small {
  font-family: 'Zodiak', serif;
  font-weight: 400;
  font-size: 12px;
  line-height: 1.5;
  letter-spacing: 0;
}
```

### Key Typography Rules

- ALL Geoform text is uppercase (`text-transform: uppercase`)
- ALL Zodiak text is sentence case (no transform)
- Geoform letter-spacing is either 4% (0.04em) for large/CTA sizes or 6% (0.06em) for small label sizes
- Zodiak has zero letter-spacing
- No italic styles appear in the Figma file

---

## Layout

### Page Dimensions

| Token | Value | Notes |
|-------|-------|-------|
| Page width (desktop) | 1440px | Figma artboard width |
| Content padding (horizontal) | 104px | Left/right page margin to content |
| Content max-width | ~1232px | 1440px - (2 x 104px) |

### Breakpoints

Not explicitly defined in Figma. Mobile designs exist at standard mobile widths. Recommended breakpoints:

| Breakpoint | Width | Notes |
|------------|-------|-------|
| Mobile | < 768px | Mobile Homepage template exists |
| Tablet | 768px - 1023px | Interpolate between mobile/desktop |
| Desktop | >= 1024px | Main Figma artboard at 1440px |

---

## Spacing

Spacing values observed in Figma components (may not be exhaustive):

| Usage | Value |
|-------|-------|
| Nav link gap | 24px |
| Dropdown icon gap (from label) | 8px |
| Footer logo-to-address gap | 16px |
| Footer link gap | 24px |
| Footer social icon gap | ~16px (48.333px / 3 icons) |
| Footer bottom row padding | 40px horizontal |
| Footer links padding | 54px right |
| Footer top row inner padding | 24px |
| Logo grid title to logos | ~70px |

---

## Border Radius

| Token | Value | Usage |
|-------|-------|-------|
| --radius-button | 8px | Buttons, email field, card corners |
| --radius-image | 24px | Carousel/hero images with rounded corners |
| --radius-search | 22px | Search input pill shape (approx) |

```css
:root {
  --radius-button: 8px;
  --radius-image: 24px;
  --radius-search: 22px;
}
```

---

## Components

### Buttons

Four button variants extracted from Figma (node 904:746):

| Variant | Background | Border | Text Color | Hover |
|---------|-----------|--------|------------|-------|
| Primary (Default) | --secondary-red (#ff595a) | none | --black | bg changes to #ffaeaf |
| Primary (Hover) | #ffaeaf | none | --black | - |
| Secondary | transparent | 1px solid --secondary-red (#ff595a) | --black | TBD |
| Style4 | transparent | 1px solid #ffaeaf | --black | TBD |

**Button dimensions:**
- Height: 40px
- Padding: 12px vertical, 20px horizontal
- Border radius: 8px
- Text: CTA style (Geoform Medium, 12px, uppercase, 0.04em tracking)

```css
.btn {
  height: 40px;
  padding: 12px 20px;
  border-radius: 8px;
  font-family: 'Geoform', sans-serif;
  font-weight: 500;
  font-size: 12px;
  line-height: 1;
  letter-spacing: 0.04em;
  text-transform: uppercase;
  cursor: pointer;
  display: inline-flex;
  align-items: center;
  justify-content: center;
}

.btn-primary {
  background-color: var(--secondary-red);
  border: none;
  color: var(--black);
}
.btn-primary:hover {
  background-color: var(--button-hover);
}

.btn-secondary {
  background-color: transparent;
  border: 1px solid var(--secondary-red);
  color: var(--black);
}

.btn-style4 {
  background-color: transparent;
  border: 1px solid var(--button-hover);
  color: var(--black);
}
```

### Promo Bar

Three variants (node 904:532):

| Variant | Background | Text Color | Close Icon Color |
|---------|-----------|------------|------------------|
| Default | --secondary-yellow (#fcd199) | --primary-blue (#005cba) | --primary-blue |
| Variant2 | --secondary-red (#ff595a) | --black | --black |
| Variant3 | --primary-blue (#005cba) | --white | --white |

**Promo bar dimensions:**
- Height: 40px
- Full width (1440px)
- Text: CTA style (Geoform Medium, 12px, uppercase, centered)
- Close icon: 16px utility icon, right-aligned at ~1.25% from right edge

### Navigation

Two variants (node 904:688):

**Default Navigation:**
- Total height: 120px (40px promo bar + 80px nav bar)
- Nav bar: white background
- Logo: 183px x ~31px, positioned at 104px from left
- Interior links: Geoform Medium, 12px, uppercase, --primary-blue, 24px gap
- Links: Tent Rentals (dropdown), Product Rentals (dropdown), Event Types (dropdown), About, Request A Quote
- Secondary links (right): Search, Account, Cart (0)
- Dropdown caret: 16px utility icon, 8px gap from link text

**With Breadcrumbs:**
- Total height: 152px (120px nav + 32px breadcrumbs)
- Breadcrumb bar: white bg, 1px solid --background-gray top and bottom borders
- Breadcrumb text: Zodiak Regular, 12px, --primary-blue, underlined links
- Separator: " / "

### Footer

Desktop footer (node 904:359):

**Dimensions:**
- Height: 207px
- Full width (1440px)
- Background: gradient (#0c6bcd to #387fd7)

**Top row:**
- Logo lockup: Logo (183px x ~31px) + address below (16px gap)
- Address: Zodiak Regular, 12px, white, "22 Harbor Park Drive, Port Washington NY 11050"
- Newsletter email field: 387px x 59px, rounded 8px, black bg at 30% opacity
  - Label: "Join our newsletter" (Zodiak Regular, 12px, white)
  - Placeholder: "Email address" (Zodiak Regular, 15px, white at 40% opacity)
  - Submit: caret icon (rotated 90deg)

**Divider:** 1px line, full width with ~1.11% margins

**Bottom row:**
- Copyright: Zodiak Regular, 12px, white
- Footer links: Geoform Medium, 12px, uppercase, white, 24px gap
  - Links: Rental Catalog, Event Type, Careers, Contact, Tents, Services, About, Resources
- Social icons: 16px, white (Instagram + LinkedIn)

### Logo Grid

Section background: --background-taupe (#fdfcf8)

**Dimensions:**
- Height: 198px
- Full width (1440px)

**Content:**
- Title: "TRUSTED BY THE BEST" - display 3 style (Geoform Medium, 14px, uppercase, --primary-blue, 0.06em tracking)
- Logos: 8 variants that rotate/fade (auto-carousel), displayed at 30% opacity (grayscale effect)
- Logo vertical position: ~100px from top
- Clients shown: Apple, NBCUniversal, NYU, Viacom, and others

### Email Field

Newsletter signup component used in footer (node 904:1008):

- Width: 387px, Height: 59px
- Background: black at 30% opacity
- Border radius: 8px
- Label: Zodiak Regular, 12px, white, positioned top-left
- Placeholder: Zodiak Regular, 15px, white at 40% opacity
- Submit caret: 16px utility icon, right-aligned

---

## Design Directions

The Figma file contains two design directions:

**Direction A (Primary - fully built out):**
- Bold, image-forward
- Geoform + Zodiak typography
- Full component library (all components above)
- All 6 page templates (D + M)
- This is the direction to build

**Direction B (Secondary - partially explored):**
- Warm, serif-forward, elegant
- Different visual feel
- Less built out (fewer components)
- Likely an alternative pitch concept, not for development

Build from Direction A exclusively.

---

## Figma Node Reference

| Component | Node ID | Variants |
|-----------|---------|----------|
| Homepage (D) | 904:382 | 1 |
| Blog LP (D) | 904:442 | 1 |
| Blog Detail (D) | 904:467 | 1 |
| Event Type Landing (D) | 912:2416 | 1 |
| Event Detail (D) | 912:2448 | 1 |
| Mobile Homepage | 904:1040 | 1 |
| Navigation | 904:688 | Default, With Breadcrumbs |
| Footer (D) | 904:359 | 1 |
| Footer (M) | 904:1291 | 1 |
| Promo Bar | 904:532 | Default, Variant2, Variant3 |
| Buttons | 904:746 | Primary, Secondary, Style4 (each: Default, Hover) |
| Logo Grid | 904:755 | 8 (rotating logo variants) |
| Email Field | 904:1008 | Default |

---

## Implementation Notes

- Geoform and Zodiak are not standard web fonts. Source and licensing must be confirmed before development. Check if client has already licensed these or if they're included in the design agency's deliverables.
- The current WordPress site uses Agenda (via Typekit). The new design replaces Agenda entirely with Geoform + Zodiak.
- All icon assets are SVG (utility icons: caret, close, search; social icons: Instagram, LinkedIn). Export from Figma as needed.
- The footer gradient is a simple left-to-right linear gradient. CSS `linear-gradient(to right, #0c6bcd, #387fd7)` reproduces it exactly.
- Logo grid logos appear at 30% opacity. They may be using mask/blend-mode techniques in Figma, but a simple `opacity: 0.3; filter: grayscale(1)` on the logo images achieves the same visual effect.
