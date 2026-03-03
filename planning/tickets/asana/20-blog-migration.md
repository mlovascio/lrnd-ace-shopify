# ACE: Blog and Content Migration

**Classification:** Data Migration
**Dependencies:** #12 Blog Landing Page, #13 Blog Article Template

---

# Deliverable

Migrate blog content from WordPress to Shopify. Import posts with preserved titles, body content, featured images, publish dates, categories (as tags), and SEO metadata.

---

# Content Volume

- **Total blog posts:** 296
- **Published:** 231
- **Drafts:** 61
- **Other statuses:** 4

---

# Import Steps

## 1. WordPress Export
- Export blog posts via WordPress XML export (WP Admin > Tools > Export)
- Or use WP-CLI: `wp export --post_type=post`
- Extract: title, slug, body HTML, featured image URL, publish date, categories, tags, author, Yoast SEO fields

## 2. Transform to Shopify Format
- Python script to convert WordPress XML/CSV to Shopify blog import format
- Shopify blog fields: Title, Body HTML, Published At, Tags, Author, Image, SEO Title, SEO Description
- Map WordPress categories to Shopify blog tags
- Preserve HTML formatting in body content
- Update internal links from WordPress URLs to Shopify URLs

## 3. Image Handling
- Featured images: import by URL (Matrixify or manual CSV)
- In-body images: initially reference WordPress URLs, then migrate to Shopify CDN
- Identify broken images during import validation

## 4. Matrixify Import
- Use Matrixify's blog article import capability
- Map fields to Matrixify column headers
- Dry-run, validate, then execute

---

# Technical Notes

- Shopify blogs are simpler than WordPress: no categories (only tags), single author model
- WordPress category hierarchy flattens to Shopify tags
- Body HTML may contain WordPress shortcodes that need stripping or converting
- Divi shortcodes in blog posts need conversion to standard HTML
- Internal links (to other posts, pages, products) need URL rewriting

---

# Files to Create

- `scripts/transform-blog.py` - WordPress to Shopify blog CSV transform
- `planning/data-migration/blog-field-mapping.md` - Field mapping documentation

---

# Acceptance Criteria

- [ ] 231 published blog posts imported to Shopify
- [ ] Post titles, body content, and featured images preserved
- [ ] Publish dates maintained
- [ ] WordPress categories converted to Shopify tags
- [ ] SEO titles and descriptions imported from Yoast
- [ ] No WordPress/Divi shortcodes visible in rendered content
- [ ] Internal links updated to Shopify URL structure
- [ ] Spot-check 20 posts for content fidelity

---

# Reference Docs

- `planning/extraction-summary.md` - Blog post inventory
