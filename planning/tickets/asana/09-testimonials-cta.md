# ACE: Build Testimonials and CTA Section

**Classification:** Homepage Section Build
**Dependencies:** #03 Global Components
**Figma Node:** 904:384

---

# Deliverable

Create a custom Shopify section (`sections/ace-testimonials-cta.liquid`) that combines the testimonial carousel with the "Ace Every Event" CTA. In Figma these function as a unified section with the large display heading, testimonial cards, and a closing CTA button.

---

# Design Specs

## Desktop

**Layout:**
- Full viewport width, white background
- Content centered within 1232px max-width
- Three distinct content zones stacked vertically:
  1. Display heading
  2. Testimonial card carousel
  3. CTA button

**Display Heading:**
- "ACE EVERY EVENT" - displaySuper style (Geoform Medium, 100px, uppercase, 0.04em tracking, #063666)
- Centered horizontally
- This is the largest text on the entire homepage

**Testimonial Carousel:**
- 3-card layout: center card is active (full opacity), left and right cards at 20% opacity
- Active card is slightly larger or elevated compared to flanking cards
- Each card contains:
  - Quote text: paragraph style (Zodiak Regular, 15px, #063666)
  - Attribution: client name and/or event type in display-3 style (Geoform Medium, 14px, uppercase)
  - Optional: star rating or decorative quote marks
- Carousel navigation: left/right arrows or swipe
- Cards slide horizontally, center card always highlighted

**CTA Button:**
- "REQUEST A QUOTE" - secondary/outlined button style
- Transparent bg, 1px border (red #ff595a or light #ffaeaf), black text
- Centered below testimonial carousel
- 8px border radius
- Links to quote/contact page

## Mobile (375px width)

- Display heading reduces to ~50px (display-1 size)
- Single testimonial card visible at a time (swipeable)
- Side cards hidden or peeking slightly at edges
- CTA button full width
- Overall section padding reduces

---

# Current Site Reference

The current acepartyrental.com has testimonial content scattered across the site:
- Client quotes on service pages
- Event-specific testimonials
- Some reviews displayed via plugin

Testimonial content to populate:
- Source from existing client testimonials on the current site
- Confirm with LRND which testimonials to feature on the homepage
- Minimum 3 testimonials needed for the carousel, recommended 5-7 for rotation

The "Request a Quote" CTA is a core action throughout the current site - this should link to the main quote/contact form.

---

# Technical Notes

## Shopify Section Architecture
- Create as `sections/ace-testimonials-cta.liquid` with JSON schema
- Section settings: heading text (default "ACE EVERY EVENT"), CTA button text, CTA button link, CTA button style
- Use section blocks for testimonial cards (type: "testimonial")
- Each testimonial block: quote text, attribution name, attribution detail (event type/company), optional rating
- Block limit: 10 testimonials

## Carousel Implementation
- Center-focused carousel (active card emphasized, flanking cards dimmed)
- CSS approach: flexbox with overflow hidden, transform translateX for sliding
- Active card: `opacity: 1; transform: scale(1);`
- Flanking cards: `opacity: 0.2; transform: scale(0.9);`
- Transition: `transition: all 0.4s ease;`
- Vanilla JS for navigation and auto-advance
- Touch/swipe support for mobile (pointer events or touch events)

## Display Heading Performance
- 100px text is visually massive - ensure Geoform font loads before render or use font-display: swap to prevent layout shift
- If Geoform is not yet available, Montserrat fallback will render at 100px (acceptable but less impactful)

## Accessibility
- Carousel should be keyboard navigable (arrow keys for prev/next)
- `aria-live="polite"` on the active card container
- `aria-roledescription="carousel"` on the carousel wrapper
- Individual cards: `role="group"` with `aria-label="Testimonial X of Y"`
- CTA button should have clear focus state

---

# Files to Create

- `sections/ace-testimonials-cta.liquid` - Section with schema and blocks
- `assets/ace-testimonials-cta.css` - Section styles
- `assets/ace-testimonials-cta.js` - Carousel behavior (slide, swipe, keyboard)

---

# Acceptance Criteria

- [ ] Display heading "ACE EVERY EVENT" renders at 100px displaySuper style
- [ ] 3-card carousel: center card at full opacity, flanking cards at 20%
- [ ] Active card is visually prominent (scale or elevation)
- [ ] Carousel slides between testimonials with smooth animation
- [ ] Touch/swipe support on mobile
- [ ] Each testimonial displays quote text and attribution
- [ ] CTA button "REQUEST A QUOTE" renders in outlined/secondary style
- [ ] CTA button links to quote/contact page
- [ ] Testimonial blocks editable in Shopify customizer
- [ ] Mobile: heading reduces to ~50px, single card visible, button full width
- [ ] Keyboard navigation works (arrow keys, tab)
- [ ] Carousel meets accessibility requirements (aria-live, roles)

---

# Reference Docs

- `planning/design-tokens-spec.md` - Typography scale (displaySuper: 100px)
- Figma: 904:384 (Testimonials and CTA section)
- Current site: https://acepartyrental.com (testimonial content)
