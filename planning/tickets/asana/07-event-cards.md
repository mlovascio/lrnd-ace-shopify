# ACE: Build Event Cards Section

**Classification:** Homepage Section Build
**Dependencies:** #03 Global Components
**Figma Node:** 904:411

---

# Deliverable

Create a custom Shopify section (`sections/ace-event-cards.liquid`) for the "Our Events" four-card grid. Each card features an organic-masked image with a blurred icon badge overlay.

---

# Design Specs

## Desktop

**Layout:**
- Full viewport width
- Section heading: "OUR EVENTS" - display-1 style (Geoform Medium, 50px, uppercase, 0.04em tracking, #063666)
- Four cards in a horizontal row
- Each card: 268px wide
- Gap between cards: 32px
- Content centered within 1232px max-width

**Card Structure:**
- Image with organic blob mask (consistent with hero and two-up sections)
- Blurred circular icon badge: 44px diameter, centered on image, backdrop-blur effect
- Category icon inside badge (white, ~20px)
- Category label below image: display-3 style (Geoform Medium, 14px, uppercase, 0.06em tracking, #063666)

**Four Categories:**
1. Corporate Events (briefcase or building icon)
2. Weddings (rings or heart icon)
3. Film and Production (camera or film icon)
4. Educational (graduation cap or book icon)

**Visual Treatment:**
- Organic blob mask on each image (smaller version of the hero/two-up masks)
- Icon badge: frosted glass effect using `backdrop-filter: blur(22px)` with semi-transparent white bg
- Badge sits at center of image area
- Cards may have hover state (slight scale or shadow)

## Mobile

- Cards switch to 2x2 grid or horizontal scroll
- Card width adjusts to fit 2 per row with gap
- Maintain blob mask and badge treatment at smaller scale
- Section heading reduces in size

---

# Current Site Reference

The current acepartyrental.com has an "Our Events" section showcasing event types:
- Corporate Events
- Weddings
- Film and Production
- Educational Events
- Additional categories may exist (galas, non-profit, etc.)

Each card links to an event type landing page with details and photo galleries. Map these to the Event Type Landing template (#14) or collection pages on the new Shopify store.

---

# Technical Notes

## Shopify Section Architecture
- Create as `sections/ace-event-cards.liquid` with JSON schema
- Section settings: heading text, number of columns (default 4)
- Use section blocks for individual cards (type: "event_card")
- Each card block: image, icon (SVG upload or icon picker), label text, link URL
- Block limit: 8 cards maximum

## Icon Badge Implementation
- 44px circle with backdrop-filter blur
- `backdrop-filter: blur(22px); -webkit-backdrop-filter: blur(22px);`
- Background: `rgba(255, 255, 255, 0.2)` or similar semi-transparent white
- Center icon (SVG) at ~20px size, white fill
- Fallback for browsers without backdrop-filter: solid semi-transparent bg

## Blob Mask
- Reuse blob mask technique from hero (#04) and two-up (#06)
- May use a shared snippet if the shape is consistent
- Smaller-scale version for 268px card images

## Icon Assets
- Export category icons from Figma as SVG
- Or use a simple icon set (Lucide, Heroicons) for standard category icons
- Store as Shopify assets or inline SVG in Liquid

---

# Files to Create

- `sections/ace-event-cards.liquid` - Section with schema and blocks
- `assets/ace-event-cards.css` - Section styles including badge blur
- SVG icon assets for each category (or inline in Liquid)

---

# Acceptance Criteria

- [ ] Section heading "OUR EVENTS" renders in display-1 style
- [ ] Four cards display in horizontal row on desktop
- [ ] Each card has an image with organic blob mask
- [ ] Blurred icon badge (44px, backdrop-filter blur) centered on each image
- [ ] Category icons render inside badges
- [ ] Category labels below images in display-3 style
- [ ] Cards are editable in Shopify customizer (image, icon, label, link)
- [ ] Mobile: cards reflow to 2x2 grid or horizontal scroll
- [ ] Backdrop-filter has appropriate fallback
- [ ] Cards link to event type pages
- [ ] Hover state provides visual feedback

---

# Reference Docs

- `planning/design-tokens-spec.md` - Typography and color values
- Figma: 904:411 (Event Cards section)
- Current site: https://acepartyrental.com (Our Events section)
