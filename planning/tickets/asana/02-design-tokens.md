# ACE: Design Tokens and Brand CSS Layer

**Classification:** Foundation
**Dependencies:** #01 Shopify Store Setup
**Status:** COMPLETE

---

# Deliverables

Apply Ace brand identity to Dawn theme via CSS custom properties and override files:

- `ace-brand.css` (274 lines) - Core brand token layer with CSS custom properties, typography scale, button variants, heading overrides, responsive breakpoints
- `ace-fonts.liquid` snippet - Font loading for Zodiak (Fontshare CDN) and Geoform placeholder (@font-face ready for .woff2 files)
- `settings_data.json` - 5 color schemes configured with Ace brand palette
- `theme.liquid` updated to include font snippet and brand CSS

---

# Design Token Summary

## Colors
- Primary Blue: #005cba (nav, headings, links)
- Secondary Red: #ff595a (buttons, CTAs)
- Text Blue: #063666 (body text, dark headings)
- Background Taupe: #fdfcf8 (alternating sections)
- Footer Gradient: linear-gradient(to right, #0c6bcd, #387fd7)

## Typography
- Geoform Medium (500) - uppercase headings, nav, buttons, labels
- Zodiak Regular (400) - body text, paragraphs, breadcrumbs

## Layout
- Page width: 1440px artboard, 1400px Shopify setting (closest valid step)
- Content max-width: ~1232px (1440 minus 2x 104px padding)
- Button radius: 8px
- Image radius: 24px

---

# Color Schemes in settings_data.json

- scheme-1: White bg, #063666 text, #ff595a button, #005cba secondary
- scheme-2: #fdfcf8 taupe bg, same text/button colors
- scheme-3: #005cba blue bg, white text, red button (footer)
- scheme-4: #063666 dark blue bg, white text
- scheme-5: #ff595a red bg, black text

---

# Font Strategy

- **Zodiak:** Loaded from Fontshare CDN (free, no license required)
- **Geoform:** Placeholder @font-face block in ace-fonts.liquid, commented out until .woff2 files arrive from designer. Montserrat used as Shopify font picker fallback
- **Shopify picker fallbacks:** Montserrat (heading) and Lora (body) selected as closest matches to Geoform/Zodiak in Shopify's font library

---

# Acceptance Criteria

- [x] CSS custom properties defined for all brand colors
- [x] Typography utility classes match Figma scale (displaySuper, display1, display3, cta, paragraph, paragraph-small)
- [x] Button variants styled (primary, secondary, style4)
- [x] Dawn body text overrides applied (color, font, opacity)
- [x] Zodiak loads from Fontshare CDN
- [x] Geoform @font-face ready for activation when files arrive
- [x] 5 color schemes configured in settings_data.json
- [x] Brand CSS loads after Dawn base styles

---

# Reference Docs

- `planning/design-tokens-spec.md` (AUTHORITATIVE, 428 lines)
- Figma file: Mr6M1UwQ0i45tEOMHSHe6G

---

*Completed: 2026-03-02*
