# ACE: Homepage Assembly and QA

**Classification:** Integration and QA
**Dependencies:** #04 Hero Carousel, #05 Logo Grid, #06 Two-Up Services, #07 Event Cards, #08 Tabbed Content, #09 Testimonials and CTA, #10 Feature/Blog Preview

---

# Deliverable

Assemble all 7 homepage sections into the Shopify homepage template (`templates/index.json`), configure section ordering, populate with real or representative content, and perform visual QA against Figma designs.

---

# Section Stack (Top to Bottom)

Figma homepage layout (904:382):

```
1. Hero Carousel         (#04)  - Full-bleed image slider + overlay CTAs
2. Logo Grid             (#05)  - "Trusted by the Best" client logos
3. Two-Up Services       (#06)  - "Our Services" tent + catalogue cards
4. Feature/Blog Preview  (#10)  - "Dive Deeper" content card
5. Event Cards           (#07)  - "Our Events" 4-card grid
6. 40+ Years Tabbed      (#08)  - "40+ Years of Excellence" tab panels
7. Testimonials + CTA    (#09)  - "Ace Every Event" + quote CTA
```

Note: Feature/Blog Preview (#10) appears between Two-Up and Event Cards based on Figma vertical positioning. Confirm final order during assembly.

---

# Content Population

## Minimum Viable Content

Each section needs real or representative content for QA:

- **Hero:** 2-3 slides with event photos, headlines, and button links
- **Logo Grid:** 6-8 client logos (source from current site or request from LRND)
- **Two-Up:** 2 service images (tent setup, product display), links to collections
- **Feature Card:** 1 featured blog post or content piece
- **Event Cards:** 4 event categories with representative photos and icons
- **Tabbed Content:** 3 tab panels with company history content and images
- **Testimonials:** 3-5 client testimonials with attribution

## Image Sourcing

Primary sources for placeholder and real content:
- Current site (https://acepartyrental.com) - download existing hero images, event photos
- WooCommerce media export (1,703 files catalogued in extraction)
- Client-provided assets (request from LRND if needed)

---

# QA Checklist

## Visual Fidelity
- [ ] Section order matches Figma layout (904:382)
- [ ] Section spacing between components is consistent (0px per settings, or adjust)
- [ ] No visual gaps or overlapping between sections
- [ ] Overall page flow matches Figma composition

## Desktop (1440px)
- [ ] Hero: 670px height, full-bleed, overlay text legible
- [ ] Logo Grid: 198px height, taupe bg, logos at 30% opacity
- [ ] Two-Up: two equal columns, blob masks, buttons overlaid
- [ ] Feature Card: horizontal layout, gray bg, rounded corners
- [ ] Event Cards: 4 cards in row, badges with blur, labels below
- [ ] Tabbed Content: sidebar tabs left, image right, yellow accent bg
- [ ] Testimonials: 100px heading, 3-card carousel, CTA button

## Mobile (375px)
- [ ] Hero adapts to mobile height, buttons stack
- [ ] Logo Grid: logos reflow or scroll
- [ ] Two-Up: columns stack vertically
- [ ] Feature Card: stacks vertically
- [ ] Event Cards: 2x2 grid or horizontal scroll
- [ ] Tabbed Content: tabs above image, full width
- [ ] Testimonials: single card visible, swipeable

## Performance
- [ ] Lighthouse Performance score > 90 on mobile
- [ ] LCP < 2.5s (hero image is LCP element)
- [ ] CLS < 0.1 (no layout shifts from font loading or image loading)
- [ ] Total page weight < 2MB (images optimized)
- [ ] All below-fold images lazy loaded

## Functionality
- [ ] Hero carousel auto-advances and pauses on hover
- [ ] All buttons link to correct destinations
- [ ] Tab navigation works (click and keyboard)
- [ ] Testimonial carousel slides and swipes
- [ ] Logo grid animation runs smoothly

---

# Technical Notes

## templates/index.json Structure

Shopify Online Store 2.0 uses JSON templates. The homepage template lists sections in order:

```json
{
  "sections": {
    "hero": { "type": "ace-hero-carousel", "settings": {...} },
    "logos": { "type": "ace-logo-grid", "settings": {...} },
    "services": { "type": "ace-two-up", "settings": {...} },
    "feature": { "type": "ace-feature-card", "settings": {...} },
    "events": { "type": "ace-event-cards", "settings": {...} },
    "history": { "type": "ace-tabbed-content", "settings": {...} },
    "testimonials": { "type": "ace-testimonials-cta", "settings": {...} }
  },
  "order": ["hero", "logos", "services", "feature", "events", "history", "testimonials"]
}
```

## Section Spacing
- `settings_data.json` currently has `spacing_sections: 0`
- Individual sections manage their own padding (top/bottom)
- Ensure consistent vertical rhythm between sections
- Target: 80px between sections on desktop, 48px on mobile

---

# Files to Create/Modify

- `templates/index.json` - Homepage template with section stack
- Potentially adjust individual section CSS for inter-section spacing

---

# Acceptance Criteria

- [ ] All 7 custom sections render in correct order on homepage
- [ ] Each section is populated with real or representative content
- [ ] Desktop layout matches Figma composition (904:382)
- [ ] Mobile layout matches Figma mobile (904:1040)
- [ ] All interactive elements function (carousel, tabs, buttons)
- [ ] Lighthouse mobile performance > 90
- [ ] LCP < 2.5 seconds
- [ ] No console errors
- [ ] Page renders correctly in Chrome, Safari, and Firefox

---

# Reference Docs

- `planning/design-tokens-spec.md` - Design system values
- Figma: 904:382 (Desktop Homepage), 904:1040 (Mobile Homepage)
- Current site: https://acepartyrental.com (content and image source)
- Individual section tickets: #04-#10
