# ACE: Cart/Estimate Page

**Classification:** Commerce Build
**Dependencies:** #16 Product Page Template

---

# Deliverable

Style the Shopify cart page and drawer with Ace branding and "Estimate" terminology. If the quote app supports it, implement dual-mode display separating priced items from estimate items.

---

# Terminology Overrides

Ace uses "Estimate" instead of "Cart" for quote-based products. Apply via Shopify locale overrides (`locales/en.default.json`):

- "Cart" becomes "Your Estimate"
- "Add to Cart" becomes "Add to Estimate" (on quote-only products)
- "Checkout" may need adjustment depending on quote app workflow
- Standard priced items keep "Add to Cart" / "Cart" terminology

---

# Design Specs

No Figma design exists for the cart. Style Dawn's cart drawer and page with Ace brand tokens:

- Cart drawer (per settings_data.json `cart_type: "drawer"`)
- Line items: product image (8px radius), title (Geoform), quantity, price/quote label
- Estimate items: show "Quote" badge instead of price
- Priced items: show standard price and quantity controls
- CTA buttons: Ace primary button style for checkout
- Totals area: Zodiak Regular for price display

---

# Technical Notes

## Dawn Cart Implementation
- Dawn already supports cart drawer (`cart_type: "drawer"` is configured)
- Cart page: `templates/cart.json` and `sections/main-cart-*.liquid`
- Override styling with `assets/ace-cart.css`

## Dual Mode Cart
- Depends heavily on which quote app is selected (#16 blocker)
- Some quote apps maintain a separate "quote cart" alongside Shopify's cart
- Others inject into the standard cart with special line item properties
- Build the standard cart styling first, then adapt for the quote app's approach

## Locale Overrides
- Shopify's locale system allows text customization
- Modify `locales/en.default.json` for site-wide text changes
- Quote-specific terminology may need conditional Liquid logic

---

# Files to Create/Modify

- `assets/ace-cart.css` - Cart page and drawer brand styles
- `locales/en.default.json` - Terminology overrides (Estimate language)
- Modify cart sections as needed for quote app integration

---

# Acceptance Criteria

- [ ] Cart drawer opens with Ace brand styling
- [ ] Line items display with branded typography and image styling
- [ ] "Estimate" terminology applied via locale overrides
- [ ] CTA buttons use Ace primary style
- [ ] Quote items display appropriately (no price, "Quote" badge)
- [ ] Priced items display with standard price and quantity
- [ ] Mobile: cart drawer/page fully functional
- [ ] Quote app integration works (depends on app selection)

---

# Blockers

- **Quote app selection:** Cart behavior depends on which quote app is chosen. Resolve in #16 first.

---

# Reference Docs

- `planning/design-tokens-spec.md` - Button and typography styles
- `planning/extraction-summary.md` - Pricing breakdown (93.3% quote-only)
