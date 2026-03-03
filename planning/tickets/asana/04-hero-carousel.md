# ACE: Build Hero Carousel Section

**Classification:** Homepage Section Build
**Dependencies:** #03 Global Components
**Figma Node:** 904:429 (Desktop), 904:1040 (Mobile)

---

# Deliverable

Create a custom Shopify section (`sections/ace-hero-carousel.liquid`) for the homepage hero. This is a full-bleed image carousel with overlay text, organic blob-shaped image masks, and dual CTA buttons.

---

# Design Specs

## Desktop (1440x670px)

**Layout:**
- Full viewport width, 670px height
- Background image fills container with organic blob mask (irregular rounded shape, not rectangular)
- Content overlaid on left side with gradient overlays for text legibility

**Content Stack (left-aligned, over image):**
- Pre-heading label: "ACE PARTY & TENT" - display-3 style (Geoform Medium, 14px, uppercase, 0.06em tracking, white)
- Headline: "PREMIER FULL-SERVICE EVENT AND TENT RENTAL COMPANY" - display-1 style (Geoform Medium, 50px, uppercase, 0.04em tracking, white)
- Subtext: "Since 1984" or similar tagline - paragraph style (Zodiak Regular, 15px, white)
- Two buttons side-by-side:
  - Primary: "OUR SERVICES" - red bg (#ff595a), black text, 8px radius
  - Secondary: "REQUEST A QUOTE" - white bg, black text, 8px radius

**Visual Treatment:**
- Background image uses organic/blob mask shape (not a simple rectangle - has soft curved edges)
- Left-side gradient overlay: dark-to-transparent for text readability
- Bottom gradient overlay: subtle fade to white for transition to next section

**Carousel Behavior:**
- Multiple slides (content + image change per slide)
- Auto-advance with pause on hover
- Navigation dots or arrows (TBD from current site behavior)

## Mobile (375x600px)

**Layout:**
- Full width, ~600px height
- Image stacks above content OR content overlays image (narrower layout)
- Headline reduces to 32px
- Buttons stack vertically at full width
- Same gradient overlay treatment

---

# Current Site Reference

The current acepartyrental.com homepage uses a RevSlider hero carousel with:
- 3-4 rotating slides
- Full-bleed background images of event setups (tents, tables, decor)
- Headline overlay text with CTA buttons
- Auto-advancing with dot navigation

Content from current slides (to be confirmed/updated):
- Slide 1: "Premier Full-Service Event and Tent Rental Company" + services CTA
- Slide 2: Corporate events focus
- Slide 3: Wedding events focus
- Additional slides may feature seasonal content

---

# Technical Notes

## Shopify Section Architecture
- Create as `sections/ace-hero-carousel.liquid` with JSON schema
- Use Shopify section blocks for individual slides (type: "slide")
- Each slide block: image, pre-heading, headline, subtext, button 1 text/link, button 2 text/link
- Section settings: auto-advance toggle, slide duration (default 5s), max slides (limit: 6)

## Image Handling
- Hero images are LCP-critical - use `loading="eager"` on first slide image
- Lazy load subsequent slide images
- Organic blob mask: implement with CSS `clip-path` or SVG mask overlay
- Recommended image size: 1440x670px minimum, 2x for retina
- Use Shopify's image_tag with srcset for responsive sizes

## CSS Approach
- Create `assets/ace-hero-carousel.css` loaded by the section
- Use CSS custom properties from ace-brand.css
- Gradient overlays via `::before` / `::after` pseudo-elements
- Blob mask shape: define as SVG clipPath or CSS clip-path polygon
- Carousel: CSS scroll-snap or vanilla JS slider (no dependencies)

## Accessibility
- Carousel should pause on hover and focus
- Include prev/next buttons (not just dots) for keyboard navigation
- Slides should use `aria-live="polite"` for screen readers
- All images need descriptive alt text
- Ensure text over images meets WCAG AA contrast (gradient overlay helps)

---

# Files to Create

- `sections/ace-hero-carousel.liquid` - Section with schema and blocks
- `assets/ace-hero-carousel.css` - Section styles
- `assets/ace-hero-carousel.js` - Carousel behavior (auto-advance, navigation)

---

# Acceptance Criteria

- [ ] Section renders at full viewport width, 670px height on desktop
- [ ] Background images display with organic blob mask shape
- [ ] Gradient overlays provide text readability over any image
- [ ] Pre-heading, headline, subtext, and two buttons render correctly
- [ ] Typography matches Figma: Geoform uppercase headings, Zodiak body
- [ ] Primary button: red bg, secondary button: white bg
- [ ] Carousel auto-advances between slides
- [ ] Carousel pauses on hover/focus
- [ ] Navigation controls (dots and/or arrows) are functional
- [ ] First slide image loads eagerly (LCP optimization)
- [ ] Mobile: layout adapts to 375px width, headline reduces to 32px
- [ ] Mobile: buttons stack vertically
- [ ] Keyboard accessible (prev/next, pause)
- [ ] Section schema allows adding/editing slides in Shopify customizer

---

# Reference Docs

- `planning/design-tokens-spec.md` - Typography and color values
- Figma: 904:429 (Desktop Homepage), 904:1040 (Mobile Homepage)
- Current site: https://acepartyrental.com (RevSlider hero)
