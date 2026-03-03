# ACE: Build Event Type Landing Template

**Classification:** Content Template Build
**Dependencies:** #03 Global Components
**Figma Node:** 912:2416

---

# Deliverable

Create a Shopify page template (`templates/page.event-type-landing.json`) for event type landing pages. Features a hero, intro copy, 4x3 grid of event type cards, and a CTA section.

---

# Design Specs

## Desktop (Figma 912:2416)

**Layout:**
- Full viewport width, white background
- Content within 1232px max-width

**Section 1 - Hero:**
- Similar treatment to blog hero
- Page title: "EVENT TYPES" or specific category - display-1 style
- Background image or color block
- Breadcrumbs above

**Section 2 - Intro Copy:**
- Centered text block
- Heading: Geoform Medium, uppercase, #063666
- Body text: Zodiak Regular, 15px, #063666, centered
- Max-width ~800px for readability

**Section 3 - Event Type Card Grid:**
- 4-column by 3-row grid (12 cards total)
- Each card:
  - Image with rounded corners (8px or 24px radius)
  - Event type name below: display-3 style (Geoform Medium, 14px, uppercase, #063666)
  - Cards link to individual event detail pages
- Gap between cards: 24-32px
- Grid is responsive: 4 columns desktop, 2 columns tablet, 1 column mobile

**Event Types (from current site):**
- Corporate Events
- Weddings
- Bar/Bat Mitzvahs
- Film and Production
- Educational
- Galas and Fundraisers
- Holiday Parties
- Outdoor Events
- Private Parties
- Sporting Events
- Trade Shows
- Additional event types as needed

**Section 4 - CTA:**
- Shared CTA section
- "REQUEST A QUOTE" or similar

## Mobile

- Card grid: 2 columns on tablet, 1 column on mobile
- Hero reduces in size
- Intro copy takes full width with padding

---

# Current Site Reference

The current site (https://acepartyrental.com/event-types) features:
- Grid of event type cards linking to individual event pages
- Each event type has its own page with galleries and descriptions
- Categories align with the rental services offered

---

# Technical Notes

## Shopify Page Template
- Create as alternate page template: `templates/page.event-type-landing.json`
- In Shopify admin, assign this template to the Event Types page
- Card grid can use section blocks for individual cards, or metafields for dynamic content
- Consider using Shopify collections as event type categories (products tagged by event type)

## Grid Implementation
- CSS Grid: `grid-template-columns: repeat(4, 1fr)`
- Responsive: `repeat(2, 1fr)` at tablet, `1fr` at mobile
- Cards use consistent aspect ratio for images (recommend 3:2 or 4:3)

---

# Files to Create

- `templates/page.event-type-landing.json` - Page template
- `sections/ace-event-grid.liquid` - Event type card grid section
- `assets/ace-event-grid.css` - Grid styles

---

# Acceptance Criteria

- [ ] Page template available in Shopify page editor
- [ ] Hero section with title and optional breadcrumbs
- [ ] Intro copy section with centered text
- [ ] 4-column grid on desktop with 12 event type cards
- [ ] Cards show image and event type label
- [ ] Cards link to event detail pages
- [ ] Grid responsive: 2 columns tablet, 1 column mobile
- [ ] CTA section renders at bottom
- [ ] Event type cards editable in Shopify customizer

---

# Reference Docs

- `planning/design-tokens-spec.md` - Typography and color values
- Figma: 912:2416 (Event Type Landing)
- Current site: https://acepartyrental.com/event-types
