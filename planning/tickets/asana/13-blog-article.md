# ACE: Build Blog Article Template

**Classification:** Content Template Build
**Dependencies:** #12 Blog Landing Page
**Figma Node:** 904:467

---

# Deliverable

Create a Shopify article template (`templates/article.json`) for individual blog posts. Features breadcrumbs, article hero, rich text body, and a "Related Stories" section.

---

# Design Specs

## Desktop (Figma 904:467)

**Layout:**
- Full viewport width, white background
- Article content within narrower reading width (~800px centered)

**Section 1 - Breadcrumbs:**
- Breadcrumb bar: white bg, 1px solid #f0f0f0 borders
- Path: Home / Blog / Article Title
- Zodiak Regular, 12px, #005cba, underlined links
- Separator: " / "

**Section 2 - Article Hero:**
- Featured image: full content width with 24px border radius
- Category tag above title: display-3 style
- Article title: display-1 style (Geoform Medium, 50px, uppercase, #063666)
- Publish date and author: paragraph-small style (Zodiak Regular, 12px)

**Section 3 - Article Body:**
- Rich text content area
- Typography for body: Zodiak Regular, 15px, 1.5 line-height, #063666
- Headings within body: Geoform Medium, uppercase
- H2: ~28-32px, H3: ~20-24px
- Images within body: 24px border radius
- Block quotes: styled with left border or indent
- Lists: standard bullets/numbers with Zodiak body font

**Section 4 - Related Stories:**
- "OTHER STORIES" or "RELATED POSTS" heading: display-3 style
- 3-column card grid (reuse ace-blog-card.liquid snippet from #12)
- Shows 3 most recent posts from same blog/tag (excluding current article)

**Section 5 - CTA:**
- Reuse CTA section (shared component)

## Mobile

- Article body takes full width with standard padding
- Related stories stack to single column
- Featured image fills width
- Title reduces in size

---

# Technical Notes

## Shopify Article Template
- `templates/article.json` configures article page sections
- Article content accessed via `{{ article.content }}` (rich text HTML)
- Related articles: iterate `blog.articles` excluding current, limit 3
- Shopify does not have native "related articles" - filter by tag or show recent

## Rich Text Styling
- Article body is Shopify's rich text editor output
- Style with descendant selectors: `.article-body h2`, `.article-body p`, etc.
- Ensure all standard HTML elements are styled (p, h2-h4, ul, ol, blockquote, img, a)
- Images in body: override with border-radius and max-width

---

# Files to Create

- `templates/article.json` - Article template configuration
- `sections/ace-article-hero.liquid` - Article hero with featured image and metadata
- `sections/ace-article-body.liquid` - Rich text content area
- `sections/ace-related-posts.liquid` - Related stories grid
- `assets/ace-article.css` - Article page styles

---

# Acceptance Criteria

- [ ] Breadcrumbs render above article with correct path
- [ ] Featured image displays with 24px border radius
- [ ] Article title in display-1 style, category and date rendered
- [ ] Article body renders rich text with proper typography
- [ ] Body headings use Geoform, body text uses Zodiak
- [ ] Images within body have rounded corners
- [ ] Related stories section shows 3 cards (reuses blog card snippet)
- [ ] CTA section renders at bottom
- [ ] Mobile: content stacks and adapts to narrow width
- [ ] Page renders correctly with actual Shopify blog article data

---

# Reference Docs

- `planning/design-tokens-spec.md` - Typography and color values
- Figma: 904:467 (Blog Detail page)
- Current site: https://acepartyrental.com/blog (example blog posts)
