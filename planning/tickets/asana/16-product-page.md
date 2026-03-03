# ACE: Product Page Template and Quote Logic

**Classification:** Commerce Build
**Dependencies:** #03 Global Components

---

# Deliverable

Create a custom Shopify product page template with conditional quote/cart logic. Products tagged `quote-only` show "Add to Estimate" and "Request Pricing." Products tagged `has-price` show standard "Add to Cart" with listed price.

---

# Quote/Cart Hybrid Logic

Ace Party has 6,735 products. Only 452 (6.7%) have actual prices. The rest are quote-based.

```liquid
{%- if product.tags contains 'quote-only' -%}
  <!-- Quote mode: "Add to Estimate" button, "Request Pricing" label -->
{%- else -%}
  <!-- Standard mode: price display + "Add to Cart" button -->
{%- endif -%}
```

## Quote Mode (93.3% of products)
- Price area shows "Request Pricing" text instead of a dollar amount
- Primary button: "ADD TO ESTIMATE" (links to quote app or adds to quote cart)
- Secondary action: "Request Quote" link to contact form
- No "Add to Cart" button in this mode

## Standard Mode (6.7% of products)
- Price displayed normally
- Primary button: "ADD TO CART" (standard Shopify behavior)
- Cart drawer opens on add

---

# Design Specs

No Figma design exists for the product page yet. Build using Dawn's default product page as the base, styled with Ace brand tokens:

- Product image: 24px border radius
- Product title: Geoform Medium, uppercase, #063666
- Price/quote label: Zodiak Regular, 15px
- Buttons: Ace button styles (primary red for main action, secondary for alternate)
- Description: Zodiak Regular, 15px body text
- Related products section at bottom

---

# Technical Notes

## Quote App Integration
- **Recommended apps:** Quotify, SA Request a Quote, or Globo Request for Quote ($10-30/mo)
- App selection should happen before this ticket is built
- The app typically provides a widget or snippet that replaces the add-to-cart button
- Tag-based conditional logic controls which mode displays

## Dawn Product Page
- Dawn's product page (`templates/product.json` and `sections/main-product.liquid`) is robust
- Override with CSS rather than rebuilding - same pattern as header/footer
- Create `assets/ace-product.css` for brand styling
- Conditional logic added via Liquid in main-product.liquid or a custom snippet

## Product Tags
- Products will be tagged during data import (#19)
- Tags: `quote-only` (default for most products) and `has-price` (for the 452 with prices)
- Tag logic should be added to import scripts

---

# Files to Create/Modify

- `assets/ace-product.css` - Product page brand styles
- `snippets/ace-product-price.liquid` - Conditional price/quote display
- Modify `sections/main-product.liquid` - Add conditional button logic
- Or create `templates/product.json` override with custom sections

---

# Acceptance Criteria

- [ ] Products tagged `quote-only` show "Request Pricing" and "Add to Estimate"
- [ ] Products tagged `has-price` show standard price and "Add to Cart"
- [ ] Product images have 24px border radius
- [ ] Typography matches Ace brand (Geoform headings, Zodiak body)
- [ ] Button styles match Ace design tokens
- [ ] Related products section renders at bottom
- [ ] Quote app integration functional (requires app to be installed)
- [ ] Mobile: product page adapts to narrow width
- [ ] Cart drawer works for standard add-to-cart products

---

# Blockers

- **Quote app selection:** Must be decided before this ticket can be fully built. Install 2-3 candidates on dev store for evaluation.

---

# Reference Docs

- `planning/design-tokens-spec.md` - Brand typography and button styles
- `planning/extraction-summary.md` - Product data overview (6,735 products, pricing breakdown)
