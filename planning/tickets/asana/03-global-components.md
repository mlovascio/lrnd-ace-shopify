# ACE: Global Components - Header, Footer, Promo Bar

**Classification:** Foundation
**Dependencies:** #02 Design Tokens and Brand CSS Layer
**Status:** COMPLETE

---

# Deliverables

Style Dawn's built-in header, footer, and announcement bar to match Ace Figma designs using CSS override files. Dawn's existing Liquid markup is preserved (dropdowns, mobile drawer, sticky header, search, newsletter validation all work out of the box).

## Header (ace-header.css, 161 lines)
- Promo bar: 40px height, Geoform 12px uppercase, #fcd199 default bg
- Nav bar: 80px min-height, white background
- Nav links: Geoform 12px uppercase, #005cba, 24px gap
- Logo: max-width 183px
- Dropdown menu: Zodiak 14px sentence case
- Mobile drawer: Geoform 14px uppercase top-level, Zodiak sub-items
- Sticky header: reduced 60px height, 140px logo
- Cart count: #ff595a red bubble

## Footer (ace-footer.css, 217 lines)
- Gradient background: #0c6bcd to #387fd7
- Top row: 2-column grid (brand info left, newsletter right)
- Newsletter field: 387px max-width, rgba(0,0,0,0.3) bg, 8px radius, 59px height
- Placeholder: Zodiak 15px white at 40% opacity
- Divider: 1px solid rgba(255,255,255,0.2)
- Bottom row: copyright (left), links (center), social (right)
- All text white, footer links inline flex row with 24px gap
- "Powered by Shopify" hidden
- Mobile: stacked column layout, centered text

## Promo Bar
- Styled via Dawn's announcement-bar section
- Text: "New York's Premier Event Rental Company Since 1984"
- Three color variants configured (default yellow, red, blue)

---

# Configuration (header-group.json)

- Logo position: middle-left
- Menu: main-menu (dropdown style)
- Sticky: on-scroll-up
- Color scheme: scheme-1
- Localization: disabled

---

# Configuration (footer-group.json)

- Blocks: brand_information + link_list (footer menu)
- Color scheme: scheme-3 (blue)
- Newsletter: enabled, heading "Join our newsletter"
- Social: enabled (Instagram linked)
- Payment icons, localization, policy links: disabled
- Padding: 40px top, 24px bottom

---

# Figma References

- Navigation: 904:688 (Default + With Breadcrumbs variants)
- Footer Desktop: 904:359
- Footer Mobile: 904:1291
- Promo Bar: 904:532 (Default, Variant2, Variant3)

---

# Acceptance Criteria

- [x] Promo bar matches Figma: 40px height, Geoform uppercase, yellow bg
- [x] Nav bar matches Figma: 80px height, logo left, nav links Geoform uppercase
- [x] Dropdown menus styled with Zodiak body font
- [x] Mobile drawer styled with brand fonts and colors
- [x] Sticky header reduces height on scroll
- [x] Footer gradient background applied
- [x] Newsletter field matches Figma: dark bg, rounded, white text
- [x] Footer bottom row: copyright, links, social in flex layout
- [x] Mobile footer stacks vertically and centers text
- [x] "Powered by Shopify" hidden

---

*Completed: 2026-03-02*
