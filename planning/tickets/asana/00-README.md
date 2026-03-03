# Asana Ticket Descriptions

> **Purpose:** Detailed ticket descriptions for copy-paste into Asana
> **Project:** Learned Media / Ace Party & Tent Rental Shopify Migration
> **Last Updated:** 2026-03-02
> **Tickets:** 23 total across 6 phases

---

# Usage

These markdown files contain detailed descriptions for each Asana ticket. Copy the content (excluding the title line) and paste into the corresponding Asana task description.

**Reference data:**
- `planning/design-tokens-spec.md` - AUTHORITATIVE design token values
- `planning/extraction-summary.md` - WordPress/WooCommerce extraction overview
- Figma file: `Mr6M1UwQ0i45tEOMHSHe6G` (6 page templates, D+M)

---

# Ticket Index

## Phase 1: Foundation (Complete)
- **#01 Shopify Store Setup & Theme Config:** No dependencies. COMPLETE
- **#02 Design Tokens & Brand CSS Layer:** Depends on #01. COMPLETE
- **#03 Global Components (Header, Footer, Promo Bar):** Depends on #02. COMPLETE

## Phase 2: Homepage Sections
- **#04 Build Hero Carousel Section:** Depends on #03. Figma: 904:429
- **#05 Build Logo Grid Section:** Depends on #03. Figma: 904:755
- **#06 Build Two-Up Services Section:** Depends on #03. Figma: 904:425
- **#07 Build Event Cards Section:** Depends on #03. Figma: 904:411
- **#08 Build 40+ Years Tabbed Content Section:** Depends on #03. Figma: 904:406
- **#09 Build Testimonials and CTA Section:** Depends on #03. Figma: 904:384
- **#10 Build Feature/Blog Preview Section:** Depends on #03. Figma: 904:418
- **#11 Homepage Assembly and QA:** Depends on #04-#10

## Phase 3: Content Page Templates
- **#12 Build Blog Landing Page Template:** Depends on #03. Figma: 904:442
- **#13 Build Blog Article Template:** Depends on #12. Figma: 904:467
- **#14 Build Event Type Landing Template:** Depends on #03. Figma: 912:2416
- **#15 Build Event Detail Template:** Depends on #03. Figma: 912:2448

## Phase 4: Product and Commerce
- **#16 Product Page Template and Quote Logic:** Depends on #03
- **#17 Collection Page Template:** Depends on #03
- **#18 Cart/Estimate Page:** Depends on #16

## Phase 5: Data Migration
- **#19 Product Data Import (Non-Linen):** Depends on #16, #17
- **#20 Blog and Content Migration:** Depends on #12, #13
- **#21 Media Migration:** Depends on all templates

## Phase 6: SEO, QA, and Launch
- **#22 URL Redirects and SEO Metadata:** Depends on all templates
- **#23 QA and Launch Prep:** Depends on all tickets

---

# Estimated Hours

| Phase | Low | High |
|-------|-----|------|
| 1. Foundation | 11 | 18 |
| 2. Homepage Sections | 34 | 50 |
| 3. Content Page Templates | 18 | 28 |
| 4. Product and Commerce | 28 | 46 |
| 5. Data Migration | 30 | 50 |
| 6. SEO, QA, and Launch | 47 | 80 |
| **Total** | **168** | **272** |

---

# Key Technical Decisions

- **Dawn v15.4.1 base theme:** Shopify Online Store 2.0, JSON templates, section architecture
- **CSS override pattern:** Custom ace-*.css files layered after Dawn base styles (no Dawn core edits)
- **Custom sections:** Each homepage component is a standalone Shopify section with its own Liquid, CSS, and JS
- **Font strategy:** Zodiak from Fontshare CDN, Geoform fallback to Montserrat until .woff2 files arrive
- **Quote workflow:** Tag-based conditional logic (quote-only vs has-price) with quote app integration

---

# Blockers

- **Geoform font files:** Need .woff2 from designer. Using Montserrat fallback
- **Product data freshness:** WooCommerce CSV is from Oct 2024, may need re-export
- **Shopify plan tier:** Standard likely sufficient, but confirm before checkout customization
- **Linen strategy:** Phased approach recommended (non-linen first, consolidate 6,140 linens later)

---

*Last Updated: 2026-03-02*
