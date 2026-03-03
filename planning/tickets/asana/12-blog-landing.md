# ACE: Build Blog Landing Page Template

**Classification:** Content Template Build
**Dependencies:** #03 Global Components
**Figma Node:** 904:442

---

# Deliverable

Create a Shopify blog template (`templates/blog.json`) for the blog landing/index page. Features a page hero, 3-column blog card grid with pagination, and a CTA section.

---

# Design Specs

## Desktop (Figma 904:442)

**Layout:**
- Full viewport width, white background
- Content within 1232px max-width (1440px minus 2x 104px padding)

**Section 1 - Page Hero:**
- Full-width hero area with background image or color
- Blog title: "RESOURCES" or "BLOG" - display-1 style (Geoform Medium, 50px, uppercase, #063666)
- Optional subheading: paragraph style (Zodiak Regular, 15px)
- Breadcrumbs above title (if using breadcrumb variant from nav)

**Section 2 - Blog Card Grid:**
- 3-column grid layout
- Card structure:
  - Featured image (top, rounded corners - 8px radius per card settings)
  - Category tag: display-3 style (Geoform Medium, 14px, uppercase, #005cba)
  - Post title: heading style (Geoform Medium, ~20-24px, uppercase, #063666)
  - Excerpt: paragraph-small style (Zodiak Regular, 12px, #063666)
  - Read more link: CTA style
- Gap between cards: 32px
- Pagination at bottom (numbered or load more)

**Section 3 - CTA Banner:**
- Reuse CTA pattern from homepage (#09) or create a shared CTA section
- "REQUEST A QUOTE" or similar call to action
- Can be the same section as the testimonials CTA or a standalone banner

## Mobile

- Blog cards stack to single column
- Hero reduces to smaller heading
- Pagination remains functional

---

# Current Site Reference

The current acepartyrental.com blog (https://acepartyrental.com/blog) has:
- 296 total blog posts (231 published, 61 draft)
- Categories include event planning tips, inspiration, corporate events, weddings
- Posts have featured images, titles, excerpts
- Standard WordPress blog pagination

---

# Technical Notes

## Shopify Blog Template
- Shopify uses `templates/blog.json` for blog index pages
- Blog articles are iterated with `{% for article in blog.articles %}`
- Pagination via `{% paginate blog.articles by 12 %}`
- Shopify handles blog/article routing natively

## Shared Components
- Consider building a `snippets/ace-blog-card.liquid` for reuse on blog index and "related posts" sections
- CTA section could be a shared section used across multiple templates

---

# Files to Create

- `templates/blog.json` - Blog template configuration
- `sections/ace-blog-hero.liquid` - Blog page hero (or reuse generic hero)
- `sections/ace-blog-grid.liquid` - Article card grid with pagination
- `snippets/ace-blog-card.liquid` - Reusable blog card component
- `assets/ace-blog-grid.css` - Grid and card styles

---

# Acceptance Criteria

- [ ] Blog landing page renders with hero, grid, and CTA sections
- [ ] 3-column card grid on desktop
- [ ] Each card shows featured image, category, title, excerpt, read more link
- [ ] Card typography matches Figma (Geoform headings, Zodiak body)
- [ ] Pagination works (12 posts per page recommended)
- [ ] Mobile: cards stack to single column
- [ ] Blog card snippet is reusable across templates
- [ ] Page loads with Shopify blog data (articles from blog)

---

# Reference Docs

- `planning/design-tokens-spec.md` - Typography and color values
- Figma: 904:442 (Blog Landing Page)
- Current site: https://acepartyrental.com/blog
