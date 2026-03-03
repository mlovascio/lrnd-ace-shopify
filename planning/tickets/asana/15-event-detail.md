# ACE: Build Event Detail Template

**Classification:** Content Template Build
**Dependencies:** #03 Global Components
**Figma Node:** 912:2448

---

# Deliverable

Create a Shopify page template (`templates/page.event-detail.json`) for individual event type pages. Features breadcrumbs, hero, partner logo grid, intro copy, masonry image gallery, and CTA.

---

# Design Specs

## Desktop (Figma 912:2448)

**Layout:**
- Full viewport width, white background
- Content within 1232px max-width

**Section 1 - Breadcrumbs:**
- Same breadcrumb bar as blog article
- Path: Home / Event Types / [Event Name]
- Zodiak Regular, 12px, #005cba

**Section 2 - Hero:**
- Event-specific hero with background image
- Event name: display-1 style (Geoform Medium, 50px, uppercase, white text over image)
- Gradient overlay for text readability

**Section 3 - Partner Logo Grid:**
- Similar to homepage logo grid (#05) but event-specific
- "TRUSTED PARTNERS" or "FEATURED CLIENTS" label
- Logos of clients who booked this event type
- Grayscale at 30% opacity

**Section 4 - Intro Copy:**
- Heading: Geoform Medium, uppercase, #063666
- Body text: Zodiak Regular, 15px, #063666
- Describes the event type and Ace's services for it
- Max-width ~800px centered

**Section 5 - Image Gallery:**
- 4x4 masonry or grid layout (16 images)
- Mixed image sizes: some span 2 columns, some are single
- Images with 24px border radius
- Showcases past events of this type
- Click to enlarge (lightbox) or browse gallery

**Section 6 - CTA:**
- Shared CTA section
- "REQUEST A QUOTE" CTA

## Mobile

- Gallery reduces to 2-column grid
- Hero adapts to mobile height
- Intro copy takes full width
- Partner logos scroll or reduce count

---

# Current Site Reference

Individual event pages on the current site include:
- Event description and services offered
- Photo gallery of past events
- Related rental categories
- Contact/quote CTA

Example pages:
- https://acepartyrental.com/event-types/corporate-events
- https://acepartyrental.com/event-types/weddings
- https://acepartyrental.com/event-types/film-production

---

# Technical Notes

## Gallery Implementation Options
- **CSS Grid masonry:** Use `grid-template-rows: masonry` (limited browser support) or manual span classes
- **Fixed grid with varied spans:** Define a 4-column grid, some images get `grid-column: span 2` or `grid-row: span 2`
- **Lightbox:** Use a lightweight vanilla JS lightbox or Shopify's built-in media viewer
- Consider using Shopify section blocks for gallery images (each block = one image with optional span settings)

## Page Template
- `templates/page.event-detail.json` as alternate page template
- One template serves all event types - content varies per page
- Gallery images managed via section blocks in Shopify customizer

---

# Files to Create

- `templates/page.event-detail.json` - Page template
- `sections/ace-event-hero.liquid` - Event-specific hero
- `sections/ace-partner-logos.liquid` - Partner/client logos (or reuse logo grid)
- `sections/ace-image-gallery.liquid` - Masonry gallery section
- `assets/ace-image-gallery.css` - Gallery layout styles
- `assets/ace-image-gallery.js` - Lightbox behavior (if needed)

---

# Acceptance Criteria

- [ ] Page template available in Shopify page editor
- [ ] Breadcrumbs render with correct path
- [ ] Hero displays event name over background image
- [ ] Partner logo grid renders with grayscale logos
- [ ] Intro copy section with heading and body text
- [ ] Gallery renders in masonry/grid layout with 24px rounded images
- [ ] Gallery supports mixed image sizes (spanning columns)
- [ ] Lightbox or enlarged view works on gallery image click
- [ ] CTA section renders at bottom
- [ ] Mobile: gallery reduces to 2-column grid
- [ ] All sections editable in Shopify customizer

---

# Reference Docs

- `planning/design-tokens-spec.md` - Typography, color, and border radius values
- Figma: 912:2448 (Event Detail page)
- Current site: https://acepartyrental.com/event-types/ (individual event pages)
