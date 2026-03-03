# ACE: Product Data Import (Non-Linen)

**Classification:** Data Migration
**Dependencies:** #16 Product Page Template, #17 Collection Page Template

---

# Deliverable

Import ~600 non-linen products from WooCommerce into Shopify using Matrixify. This is Phase 1 of the product import - linens (6,140 products) are deferred to post-launch.

---

# Data Source

- **WooCommerce CSV:** `wp-content/webtoffee_export/product_export_2024-10-10-05-07-49.csv`
- **Freshness warning:** CSV is from October 2024. May need a fresh export from WP admin for current data
- **Local WordPress:** `/Users/mlovascio/Local Sites/acepartyrental/app/public/`

---

# Product Breakdown

| Category | Count | Notes |
|----------|-------|-------|
| Total products | 6,735 | |
| Linens (deferred) | 6,140 | 91% - consolidated post-launch |
| Non-linen products | ~595 | Phase 1 import |
| Products with prices | 452 | Tagged `has-price` |
| Quote-only products | ~6,283 | Tagged `quote-only` |

---

# Import Steps

## 1. Python Transform Script
- Read WooCommerce CSV
- Filter out linen products (by category or product type)
- Map WooCommerce columns to Shopify/Matrixify format:
  - Title, Handle, Body HTML, Price, Compare At Price
  - Images (by URL - Matrixify downloads from acepartyrental.com)
  - Categories mapped to Shopify collections
  - Yoast SEO fields mapped to Shopify SEO title/description
  - SKU, Weight, Inventory
- Add tags: `quote-only` or `has-price` based on price value
- Output: Matrixify-compatible CSV

## 2. Collection Creation
- Map WooCommerce product categories to Shopify collections
- Create automated collections based on product tags/types
- Key collections: Tent Rentals, Tables, Chairs, Tabletop, Catering Equipment, Decor, Lighting, Flooring

## 3. Matrixify Import
- Install Matrixify app on dev store ($20/mo during migration)
- Upload transformed CSV
- Matrixify downloads product images from acepartyrental.com URLs
- Dry-run first to validate, then execute

## 4. Validation
- Spot-check 50 products across categories
- Verify images downloaded correctly
- Verify tags applied (quote-only vs has-price)
- Verify SEO metadata imported
- Verify collection assignments

---

# Technical Notes

- Matrixify handles image download from external URLs automatically
- Products with no price: import with price 0 or blank, rely on tag for display logic
- WooCommerce variable products: may need flattening or variant mapping
- WooCommerce custom fields: evaluate what carries over

---

# Files to Create

- `scripts/transform-products.py` - WooCommerce to Shopify CSV transform
- `planning/data-migration/field-mapping.md` - Column mapping documentation
- `planning/data-migration/collection-mapping.md` - Category to collection mapping

---

# Acceptance Criteria

- [ ] Transform script processes WooCommerce CSV without errors
- [ ] ~600 non-linen products imported to Shopify dev store
- [ ] Product images downloaded and displayed
- [ ] Tags applied: `quote-only` or `has-price` on every product
- [ ] SEO titles and descriptions imported from Yoast data
- [ ] Products assigned to correct collections
- [ ] Spot-check passes on 50 products
- [ ] No duplicate products created

---

# Blockers

- **Fresh CSV export:** October 2024 CSV may be stale. Confirm if re-export is needed from WP admin.

---

# Reference Docs

- `planning/extraction-summary.md` - Product data overview and breakdown
