# ACE: URL Redirects and SEO Metadata

**Classification:** SEO and Migration
**Dependencies:** All templates and content built

---

# Deliverable

Implement URL redirects from WordPress URL structure to Shopify URL structure. Import SEO metadata from Yoast. Set up Google Analytics and Search Console.

---

# URL Structure Changes

- Products: `/product/{slug}/` becomes `/products/{slug}`
- Categories: `/product-category/{slug}/` becomes `/collections/{slug}`
- Blog posts: `/blog/{slug}/` becomes `/blogs/news/{slug}`
- Pages: `/{slug}/` becomes `/pages/{slug}`

---

# Redirect Volume

| Source | Count | Notes |
|--------|-------|-------|
| Existing Redirection plugin rules | 396 | Already exported |
| Product URL redirects | ~600 | Non-linen products |
| Category redirects | ~30 | WooCommerce categories to collections |
| Blog post redirects | ~231 | Published posts |
| Page redirects | ~87 | WordPress pages |
| **Estimated total** | **~1,344** | |

---

# Implementation Steps

## 1. Generate Redirect CSV
- Python script to generate redirect CSV from WooCommerce product data, blog slugs, and page slugs
- Include existing 396 rules from Redirection plugin export
- Format: old_path, new_path (301 redirect)

## 2. Import to Shopify
- Shopify Admin: Settings > Navigation > URL Redirects
- Bulk import via CSV upload
- Or use Matrixify for bulk redirect import
- Shopify supports up to 200,000 URL redirects

## 3. SEO Metadata
- Yoast `_yoast_wpseo_title` mapped to Shopify SEO title on products, pages, and blog posts
- Yoast `_yoast_wpseo_metadesc` mapped to Shopify SEO description
- This should be handled during import (#19, #20) but validate here

## 4. Google Integration
- GA4: install via Shopify native integration (Online Store > Preferences)
- Google Search Console: verify new domain, submit sitemap (`/sitemap.xml`)
- Google Business Profile: update website URL after DNS cutover

---

# Technical Notes

- Shopify automatically generates `/sitemap.xml`
- Shopify handles canonical URLs natively
- Test redirects with `curl -I` to verify 301 status codes
- Monitor 404s in Shopify Analytics after launch
- Redirects are case-insensitive in Shopify

---

# Files to Create

- `scripts/generate-redirects.py` - Generate redirect CSV from all data sources
- `planning/data-migration/redirect-map.csv` - Complete redirect map

---

# Acceptance Criteria

- [ ] All 396 existing redirect rules imported
- [ ] Product URL redirects functional (~600)
- [ ] Blog post URL redirects functional (~231)
- [ ] Page URL redirects functional (~87)
- [ ] Category URL redirects functional (~30)
- [ ] Spot-check 100 redirects with `curl -I` (301 status)
- [ ] SEO titles and descriptions present on all imported content
- [ ] GA4 installed and tracking
- [ ] Google Search Console verified, sitemap submitted
- [ ] No significant 404 errors in first week post-launch

---

# Reference Docs

- `planning/extraction-summary.md` - Content inventory for redirect generation
- Existing redirects: from WordPress Redirection plugin export
