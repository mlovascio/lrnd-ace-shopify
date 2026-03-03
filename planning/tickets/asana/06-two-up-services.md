# ACE: Build Two-Up Services Section

**Classification:** Homepage Section Build
**Dependencies:** #03 Global Components
**Figma Node:** 904:425

---

# Deliverable

Create a custom Shopify section (`sections/ace-two-up.liquid`) for the "Our Services" two-column image grid. This section features two large square images with organic blob masks and overlaid CTA buttons.

---

# Design Specs

## Desktop

**Layout:**
- Full viewport width
- Section heading at top: "OUR SERVICES" - display-1 style (Geoform Medium, 50px, uppercase, 0.04em tracking, #063666)
- Two-column grid below heading
- Each column: 568x568px image area
- Gap between columns: ~32px
- Content centered within 1232px max-width

**Left Column - Tent Services:**
- Background image: tent/event photo
- Organic blob mask shape (same style as hero, irregular rounded edges)
- Overlaid button at bottom-center: "TENT SERVICES" - primary button style (red bg #ff595a, black text, 8px radius)

**Right Column - Product Catalogue:**
- Background image: rental products photo
- Organic blob mask shape
- Overlaid button at bottom-center: "PRODUCT CATALOGUE" - primary button style

**Visual Treatment:**
- Images may have subtle gradient overlay at bottom for button readability
- Blob mask creates a soft organic feel matching the hero treatment
- Both images are equal size, creating visual balance

## Mobile

- Columns stack vertically (single column)
- Images remain full-width with blob mask
- Buttons remain overlaid on images
- Section heading reduces in size

---

# Current Site Reference

The current acepartyrental.com homepage has a similar services section that links to:
- Tent Rentals category (tents, flooring, lighting, climate control)
- Product Catalogue (tables, chairs, linens, tabletop, catering equipment)

These are the two primary service categories for the business. Buttons should link to their respective collection pages on the new Shopify store.

---

# Technical Notes

## Shopify Section Architecture
- Create as `sections/ace-two-up.liquid` with JSON schema
- Section settings: heading text, heading alignment
- Two hardcoded content areas (left and right) with settings for:
  - Image upload
  - Button text
  - Button link (URL)
  - Button style (primary/secondary)
- Alternative: use section blocks for flexibility (allows 2-4 cards)

## Blob Mask Implementation
- Same organic mask technique as hero carousel (#04)
- Implement with CSS `clip-path` or SVG mask
- Consider creating a shared `snippets/ace-blob-mask.liquid` partial if the mask shape is reused across hero, two-up, and event cards
- SVG mask allows different shapes per component

## Image Handling
- Square images: recommend 1136x1136px uploads (2x for retina on 568px display)
- Use Shopify image_tag with srcset and sizes attributes
- Lazy loading appropriate (not LCP-critical since below the fold)

---

# Files to Create

- `sections/ace-two-up.liquid` - Section with schema
- `assets/ace-two-up.css` - Section styles including blob mask

---

# Acceptance Criteria

- [ ] Section heading "OUR SERVICES" renders in display-1 style
- [ ] Two-column grid with equal-sized image areas
- [ ] Both images display with organic blob mask shape
- [ ] CTA buttons overlay each image at bottom-center
- [ ] Buttons use primary style (red bg, black text, 8px radius)
- [ ] Button text and links are editable in Shopify customizer
- [ ] Images are editable in Shopify customizer
- [ ] Mobile: columns stack vertically
- [ ] Images lazy load (below the fold)
- [ ] Blob mask shape is consistent with hero section treatment

---

# Reference Docs

- `planning/design-tokens-spec.md` - Typography and button styles
- Figma: 904:425 (Two-Up Services section)
- Current site: https://acepartyrental.com (services section)
