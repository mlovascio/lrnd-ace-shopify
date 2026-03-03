# ACE: Collection Page Template

**Classification:** Commerce Build
**Dependencies:** #03 Global Components

---

# Deliverable

Create a styled collection page template for browsing product categories. Features a brand-styled grid layout with filtering and a special linen variant with color swatch UX.

---

# Design Specs

No Figma design exists for collection pages. Build using Dawn's default collection page styled with Ace brand tokens.

## Standard Collection Page
- Collection hero: collection title (Geoform Medium, uppercase, #063666) + optional description (Zodiak)
- Product grid: 3-4 columns on desktop, 2 on mobile
- Product cards:
  - Image with 8px border radius (per settings_data.json card_corner_radius)
  - Product title: Geoform Medium, 14px, uppercase
  - Price or "Request Pricing" label: Zodiak Regular, 12px
  - Quick view or add button on hover
- Filtering sidebar or top bar for category/type refinement
- Pagination or infinite scroll

## Linen Collection (Special Variant)
- Linens represent 6,140 of 6,735 products (91% of catalog)
- After consolidation, ~200-300 parent products with color variants
- Linen product cards should show color swatch dots below the product image
- Clicking a swatch updates the card image to that color variant
- Template: `templates/collection.linens.json`

---

# Technical Notes

## Dawn Collection Page
- Dawn's `sections/main-collection-product-grid.liquid` handles the grid
- Filtering uses Shopify's native storefront filtering API
- Override styling with `assets/ace-collection.css`

## Linen Swatch UX
- This is a post-launch enhancement (linens are Phase 2 of product import)
- Build the standard collection template first
- Linen template extends the standard with swatch JS and variant image switching
- Each linen product variant stores a color value and image
- Swatch display: small colored circles (12-16px) below card image

---

# Files to Create/Modify

- `assets/ace-collection.css` - Collection page brand styles
- `templates/collection.json` - Standard collection template (or modify default)
- `templates/collection.linens.json` - Linen-specific template (post-launch)
- `snippets/ace-product-card.liquid` - Styled product card (if custom needed)

---

# Acceptance Criteria

- [ ] Collection page renders with brand-styled grid
- [ ] Product cards show image (8px radius), title, and price/quote label
- [ ] Grid: 3-4 columns desktop, 2 columns mobile
- [ ] Shopify native filtering works
- [ ] Pagination functional
- [ ] Typography matches Ace brand tokens
- [ ] Collection title and description styled correctly
- [ ] Mobile: grid adapts, cards stack in 2 columns

---

# Reference Docs

- `planning/design-tokens-spec.md` - Card styles and typography
- `planning/extraction-summary.md` - Product data (6,735 products, linen breakdown)
