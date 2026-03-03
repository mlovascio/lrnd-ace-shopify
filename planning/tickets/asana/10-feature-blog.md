# ACE: Build Feature/Blog Preview Section

**Classification:** Homepage Section Build
**Dependencies:** #03 Global Components
**Figma Node:** 904:418

---

# Deliverable

Create a custom Shopify section (`sections/ace-feature-card.liquid`) for the "Dive Deeper" content preview card. This is a horizontal card component with an image on the left and content on the right, used to promote blog posts or featured content.

---

# Design Specs

## Desktop

**Layout:**
- Card container: 1167px wide, 400px tall
- Centered within 1232px max-width
- Background: #f0f0f0 (background-gray)
- Border radius: 8px on the card container
- Horizontal two-column layout inside the card

**Left Column - Image (455px wide):**
- Featured image fills left portion of card
- Image has rounded left corners (matching card radius)
- Right edge of image is flush or slightly overlapping with content
- Suggested image ratio: ~455x400px (slightly landscape)

**Right Column - Content:**
- Fills remaining width (~712px)
- Padding inside content area: ~40px
- Content stack:
  - Label: "DIVE DEEPER" or category label - display-3 style (Geoform Medium, 14px, uppercase, 0.06em tracking, #005cba)
  - Headline: article or feature title - display-1 or large heading style (Geoform Medium, ~30-40px, uppercase, #063666)
  - Excerpt: brief description - paragraph style (Zodiak Regular, 15px, #063666)
  - CTA link: "Read More" or similar - CTA style with arrow, or primary button

**Visual Treatment:**
- Clean card design with subtle gray background
- No blob mask on this component (uses rectangular card with border radius)
- Content-forward layout emphasizing the text

## Mobile

- Card stacks vertically: image on top, content below
- Image takes full card width
- Content area gets standard mobile padding
- Card width fills available space
- Headline may reduce in size

---

# Current Site Reference

The current acepartyrental.com blog section includes:
- Blog landing page with article grid
- Individual blog posts about events, tips, inspiration
- Posts are tagged by category (weddings, corporate, etc.)

This homepage section should feature the most recent or editorially selected blog post. Consider:
- Auto-populating from most recent blog post (dynamic)
- Or allowing manual selection in Shopify customizer (editorial control)
- Manual selection is recommended for homepage since not every blog post warrants homepage featuring

---

# Technical Notes

## Shopify Section Architecture
- Create as `sections/ace-feature-card.liquid` with JSON schema
- Section settings:
  - Label text (default "DIVE DEEPER")
  - Headline text (or pull from linked article)
  - Excerpt text (or pull from linked article)
  - Image upload (or pull from linked article's featured image)
  - CTA text (default "Read More")
  - CTA link (URL)
  - Optional: blog post picker (article selector) for auto-population
- Background color setting (default #f0f0f0)

## Auto-Population Option
- Shopify supports `article` picker in section schemas
- If an article is selected, pull title, excerpt, featured_image, and URL automatically
- Manual fields override auto-populated values when both exist
- This gives editors flexibility: pick an article OR manually compose the card

## CSS Approach
- Flexbox for horizontal layout, column direction on mobile
- Card uses `border-radius: 8px; overflow: hidden;` for rounded corners
- Image column: `flex: 0 0 455px;` (fixed width on desktop)
- Content column: `flex: 1;` with internal padding
- Media query at 749px switches to column direction

---

# Files to Create

- `sections/ace-feature-card.liquid` - Section with schema
- `assets/ace-feature-card.css` - Section styles

---

# Acceptance Criteria

- [ ] Card renders at ~1167x400px on desktop with 8px border radius
- [ ] Background color: #f0f0f0
- [ ] Left column: image fills 455px width, rounded left corners
- [ ] Right column: label, headline, excerpt, and CTA render correctly
- [ ] Label in display-3 style (#005cba), headline in Geoform uppercase
- [ ] Excerpt in Zodiak paragraph style
- [ ] CTA link/button is functional
- [ ] Section schema supports manual content entry
- [ ] Optional: article picker auto-populates title, excerpt, image, URL
- [ ] Mobile: card stacks vertically (image on top, content below)
- [ ] Card is lazy loaded (below the fold)

---

# Reference Docs

- `planning/design-tokens-spec.md` - Typography and color values
- Figma: 904:418 (Feature/Blog Preview section)
- Current site: https://acepartyrental.com/blog (blog content reference)
