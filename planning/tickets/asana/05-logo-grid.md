# ACE: Build Logo Grid Section

**Classification:** Homepage Section Build
**Dependencies:** #03 Global Components
**Figma Node:** 904:755

---

# Deliverable

Create a custom Shopify section (`sections/ace-logo-grid.liquid`) for the "Trusted by the Best" client logo bar. This is a full-width strip with grayscale logos that crossfade between 8 variants.

---

# Design Specs

## Desktop (1440x198px)

**Layout:**
- Full viewport width, 198px height
- Background: #fdfcf8 (background-taupe)
- Content centered horizontally within 1232px max-width

**Content:**
- Section heading: "TRUSTED BY THE BEST" - display-3 style (Geoform Medium, 14px, uppercase, #005cba, 0.06em tracking)
- Heading centered at top of section
- Logo row: ~70px below heading, horizontally distributed
- 6-8 logos displayed at a time, evenly spaced

**Logo Treatment:**
- All logos displayed at 30% opacity
- Grayscale filter applied (logos are naturally color but shown muted)
- CSS: `opacity: 0.3; filter: grayscale(1);`

**Crossfade Animation:**
- 8 logo variants in Figma (different sets of client logos)
- Logos crossfade to cycle through all clients
- Subtle transition (CSS opacity animation, ~1s fade, ~4s hold per set)

## Mobile

- Logos reduce to 4 per row or use horizontal scroll
- Section height adjusts to content
- Heading remains centered

---

# Known Clients

From Figma variants and current site:
- Apple
- NBCUniversal
- NYU (New York University)
- Viacom
- Additional logos visible in Figma variants (exact count TBD from full logo asset export)

The current acepartyrental.com site shows a similar logo bar in the upper portion of the homepage with client/partner logos. Confirm full client list with LRND before populating.

---

# Technical Notes

## Shopify Section Architecture
- Create as `sections/ace-logo-grid.liquid` with JSON schema
- Section settings: heading text (default "TRUSTED BY THE BEST"), background color
- Use section blocks for individual logos (type: "logo")
- Each logo block: image upload, alt text (client name), optional link
- Support 8-16 logos total, display 6-8 at a time

## Animation Approach
- CSS keyframe animation for crossfade (no JS library needed)
- Two rows of logos overlapping with alternating opacity
- Or: single row with CSS animation cycling through logo sets
- Simpler alternative: continuous horizontal marquee scroll (common pattern for logo bars)

## Image Handling
- Logo images should be SVG when possible (crisp at any size)
- Fallback to PNG with transparent background
- Max logo height: ~40px (scale proportionally)
- Use Shopify image_tag for automatic optimization

---

# Files to Create

- `sections/ace-logo-grid.liquid` - Section with schema and blocks
- `assets/ace-logo-grid.css` - Section styles and animation keyframes

---

# Acceptance Criteria

- [ ] Section renders at full width with #fdfcf8 background
- [ ] Heading "TRUSTED BY THE BEST" centered, display-3 style, #005cba
- [ ] Logos display at 30% opacity with grayscale filter
- [ ] Logos evenly spaced in a horizontal row
- [ ] Crossfade or marquee animation cycles through all logos
- [ ] Animation is smooth and non-distracting
- [ ] Mobile: logos reflow or scroll horizontally
- [ ] Section schema allows adding/removing logos in Shopify customizer
- [ ] Each logo has alt text for accessibility

---

# Reference Docs

- `planning/design-tokens-spec.md` - Color and typography values
- Figma: 904:755 (8 logo grid variants)
- Current site: https://acepartyrental.com (client logo section)
