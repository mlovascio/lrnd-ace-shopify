# ACE: Media Migration

**Classification:** Data Migration
**Dependencies:** All templates built

---

# Deliverable

Migrate media assets from WordPress to Shopify, including product images (handled by Matrixify in #19), blog images, page content images, and static assets (logos, icons, PDFs).

---

# Media Inventory

| Type | Count | Notes |
|------|-------|-------|
| PNG files | 837 | |
| JPEG files | 783 | |
| SVG files | 41 | Logos, icons |
| PDF files | 27 | Brochures, documents |
| Other | 15 | |
| **Total** | **1,703** | ~1.6GB estimated |

---

# Migration Strategy

## Product Images (Handled by #19)
- Matrixify downloads product images from acepartyrental.com URLs during product import
- No separate action needed for product images

## Blog Featured Images (Handled by #20)
- Imported as part of blog migration via Matrixify
- Referenced by URL during import

## In-Content Images
- Images embedded in blog post bodies and page content
- Initially: leave referencing WordPress URLs (they'll continue loading from the old host)
- Post-migration: rewrite URLs to Shopify CDN after uploading to Shopify Files
- Python script to scan all imported content HTML for image URLs and generate upload/rewrite list

## Static Assets
- Logos (SVG): upload to Shopify Files or include in theme assets
- Icons (SVG): include in theme assets
- PDFs (brochures, menus): upload to Shopify Files, update download links
- Hero images, event photos: upload to Shopify Files for section content

## Upload Method
- Shopify Files (Settings > Files): manual upload via admin
- Or Shopify CLI: bulk upload via API
- Or Matrixify: supports file imports

---

# Technical Notes

- Shopify Files has a storage limit based on plan tier (check plan)
- Maximum file size: 20MB per file
- Supported formats: JPEG, PNG, GIF, SVG, PDF, MP4, WebM
- After uploading, in-content image URLs must be rewritten from `acepartyrental.com/wp-content/uploads/...` to Shopify CDN URLs
- Consider running this after DNS cutover, so old URLs still resolve during transition

---

# Files to Create

- `scripts/scan-media-urls.py` - Scan imported content for WordPress media URLs
- `scripts/rewrite-media-urls.py` - Batch rewrite URLs to Shopify CDN paths
- `planning/data-migration/media-inventory.md` - Categorized media list

---

# Acceptance Criteria

- [ ] All static assets (logos, icons, PDFs) uploaded to Shopify
- [ ] Hero and event images available for section content
- [ ] In-content image URLs identified and documented
- [ ] URL rewriting plan established (WordPress to Shopify CDN)
- [ ] No broken images on key pages (homepage, top 20 blog posts, event pages)
- [ ] File storage within Shopify plan limits

---

# Reference Docs

- `planning/extraction-summary.md` - Media file inventory (1,703 files)
