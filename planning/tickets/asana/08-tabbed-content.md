# ACE: Build 40+ Years Tabbed Content Section

**Classification:** Homepage Section Build
**Dependencies:** #03 Global Components
**Figma Node:** 904:406, 904:546

---

# Deliverable

Create a custom Shopify section (`sections/ace-tabbed-content.liquid`) for the "40+ Years of Excellence" tabbed image showcase. This section features a sidebar tab navigation with corresponding image carousel panels.

---

# Design Specs

## Desktop

**Layout:**
- Full viewport width
- Accent background: #fdefdc (tertiary-yellow) applied to a portion or full section bg
- Content centered within 1232px max-width
- Two-column layout: sidebar tabs (left, ~30%) and image carousel (right, ~70%)

**Section Heading:**
- "40+ YEARS OF EXCELLENCE" - display-1 style (Geoform Medium, 50px, uppercase, 0.04em tracking, #063666)
- Positioned above the tab/image layout

**Sidebar Tabs (Left Column):**
- 3 tab items, stacked vertically
- Each tab: text label in Geoform Medium, uppercase
- Active tab: full opacity (100%), slightly larger or highlighted
- Inactive tabs: 30% opacity
- Tab labels relate to company history or service milestones (e.g., "Our Story", "Our Team", "Our Legacy" - exact text TBD from content)
- Clicking a tab switches the image panel on the right

**Image Panel (Right Column):**
- Large image area displaying content for the active tab
- Images may use organic blob mask (consistent with other sections)
- Smooth transition/crossfade when switching between tabs
- Image dimensions: approximately 700x500px area

**Visual Treatment:**
- Warm accent background (#fdefdc) creates visual contrast from white sections
- Tab opacity animation creates clear active/inactive distinction
- Clean, minimal layout emphasizing the imagery

## Mobile

- Tabs move above image panel (horizontal scrolling tab bar or stacked)
- Image panel takes full width
- Section heading reduces in size
- Tab labels may truncate or use shorter variants

---

# Current Site Reference

The current acepartyrental.com does not have an exact equivalent of this section. The "40+ Years" messaging appears in various places on the current site referencing the company's history since 1984. Content for tab panels will need to be sourced from:

- About page content (company history, milestones)
- Existing "About Us" imagery
- Team/leadership photos
- Event portfolio images

Confirm tab content and labels with LRND before populating.

---

# Technical Notes

## Shopify Section Architecture
- Create as `sections/ace-tabbed-content.liquid` with JSON schema
- Section settings: heading text, background color (default #fdefdc)
- Use section blocks for tabs (type: "tab")
- Each tab block: label text, image upload, optional description text
- Block limit: 5 tabs maximum

## Tab Interaction
- Vanilla JS for tab switching (no library)
- Active tab gets data attribute or class toggle
- Image panel crossfades between tab images (CSS transition on opacity)
- First tab active by default on page load
- Tab click: set active class, update aria-selected, fade image

## CSS Approach
- Flexbox or CSS Grid for sidebar + image layout
- Tab opacity transition: `transition: opacity 0.3s ease`
- Image crossfade: absolute positioning with opacity toggle
- Accent background: apply to section wrapper or inner container

## Accessibility
- Tab pattern should follow WAI-ARIA Tabs pattern
- `role="tablist"` on tab container
- `role="tab"` on each tab, `role="tabpanel"` on each panel
- `aria-selected="true/false"` on tabs
- Arrow key navigation between tabs
- Tab panels should be focusable

---

# Files to Create

- `sections/ace-tabbed-content.liquid` - Section with schema and blocks
- `assets/ace-tabbed-content.css` - Section styles
- `assets/ace-tabbed-content.js` - Tab switching behavior

---

# Acceptance Criteria

- [ ] Section heading "40+ YEARS OF EXCELLENCE" renders in display-1 style
- [ ] Accent background (#fdefdc) applied to section
- [ ] Two-column layout: sidebar tabs (left) and image (right)
- [ ] Active tab displays at full opacity, inactive tabs at 30%
- [ ] Clicking a tab switches the image panel with crossfade
- [ ] First tab is active by default
- [ ] Tab labels and images are editable in Shopify customizer
- [ ] Follows WAI-ARIA Tabs pattern (roles, aria-selected, arrow keys)
- [ ] Mobile: tabs reflow above image, full-width layout
- [ ] Image transitions are smooth (no flash or jump)
- [ ] Section schema supports 3-5 tab blocks

---

# Reference Docs

- `planning/design-tokens-spec.md` - Color and typography values
- Figma: 904:406, 904:546 (40+ Years / Tabbed Content)
- Current site: https://acepartyrental.com/about (About page for content reference)
