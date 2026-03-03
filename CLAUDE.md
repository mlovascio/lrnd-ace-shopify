# Ace Party & Tent Rental - Shopify Migration

> **Repository:** lrnd-ace-shopify
> **Purpose:** Shopify theme development for WooCommerce to Shopify migration
> **Last Updated:** 2026-03-02

---

## Project Overview

> **Client:** Ace Party & Tent Rental / Gandel family
> **Account:** LRND (Learned Media) - direct client
> **Project Type:** WooCommerce (WordPress/Divi) to Shopify migration
> **Status:** Phase 1 - Setup & Foundation
> **Budget:** 200-280 hours
> **Timeline:** 10-12 weeks
> **Asana Project GID:** 1209399682946958
> **Harvest Client ID:** 15897381

Ace Party is a B2B event rental company (tents, chairs, tables, linens, catering equipment) based in Port Washington, NY. Their current site runs WordPress/WooCommerce with a Divi child theme on WPEngine. The catalog is quote-based: 93% of products show "Request Pricing" instead of a fixed price.

New Figma designs exist for 6 content/marketing page templates. Product catalog pages (PDP, PLP, cart) will use Shopify defaults styled to match the brand.

---

## Repository Structure

```
lrnd-ace-shopify/
  CLAUDE.md                     # This file
  .gitignore
  planning/                     # Migration planning docs
    extraction-summary.md       # WordPress data extraction (COMPLETE)
    design-tokens-spec.md       # Figma design tokens (AUTHORITATIVE)
    data-migration/             # Product/content migration scripts (future)
    tickets/                    # Asana ticket specs (future)
    qa/                         # QA reports (future)
  theme/                        # Shopify theme (Dawn-based, future)
    assets/
    config/
    layout/
    locales/
    sections/
    snippets/
    templates/
  scripts/                      # Migration scripts (future)
```

---

## Migration Plan

The approved migration plan is at: `/Users/mlovascio/.claude/plans/happy-conjuring-parasol.md`

### Phase Summary

| Phase | Scope | Hours | Status |
|-------|-------|-------|--------|
| 1. Setup & Foundation | Repo, dev store, tokens, theme scaffold | 11-18 | In Progress |
| 2. Global Components | Header, footer, promo bar, buttons, base CSS | 20-30 | Pending |
| 3. Content Page Templates | Homepage, blog, event type, event detail | 34-50 | Pending |
| 4. Product & Commerce | Quote workflow, PDP, PLP, cart | 28-46 | Pending |
| 5. Data Migration | Products, blog, media import | 30-50 | Pending |
| 6. SEO & Redirects | URL mapping, redirect import, meta tags | 13-20 | Pending |
| 7. Integrations | Forms, search, Instagram, newsletter | 9-18 | Pending |
| 8. QA & Launch | Testing, DNS cutover, monitoring | 34-60 | Pending |

### Key Architecture Decisions

- **Theme base:** Shopify Dawn (Online Store 2.0, sections everywhere)
- **Hybrid quote workflow:** Product tags (`quote-only` vs `has-price`) drive conditional Liquid logic
- **Quote app:** Quotify or SA Request a Quote (evaluation pending)
- **Phased product migration:** Launch with ~537 non-linen products first, consolidate 6,140 linen color variants into ~200-400 variant-based products post-launch
- **Migration tool:** Matrixify ($20/mo during migration)

---

## Source Data

### WordPress Site

- **Production:** acepartyrental.com (WPEngine install: acepartyandten)
- **Local copy:** ~/Local Sites/acepartyrental/app/public/
- **Local MySQL:** Port 10014, socket zpIcHGqUx, DB: local, user: root/root
- **Product CSV:** wp-content/webtoffee_export/product_export_2024-10-10-05-07-49.csv (may need re-export)

### Content Inventory (from extraction)

| Content | Count | Notes |
|---------|-------|-------|
| Products | 6,677 published | 93% quote-only, 12% have images |
| Pages | 30 published | All Divi Builder, 12 event type detail pages |
| Blog Posts | 20 published | All have Yoast SEO metadata |
| Contact Forms | 2 (CF7) | Contact page + Careers |
| Navigation Menus | 2 | Main Nav (product mega menu) + Secondary |
| Redirects | 14 active | Plus ~7,000 URL pattern changes |
| Media | ~21,025 files (1.6GB) | ~1.4GB after excluding form uploads/logs |
| Quote Requests | 2,281 | Confirms quote workflow is critical |
| Testimonials | 4 | Divi Plus custom post type |

### Linen Products (91% of catalog)

6,140 products across 35 subcategories (Spun Cotton, Bengaline, Matte Satin, etc.). Each "product" is actually a color variant (e.g., "Spun Cotton - Aqua - Tablecloth 90x90"). Only ~6% have images. These will be consolidated post-launch into ~200-400 variant-based Shopify products where each color becomes a variant with a swatch.

---

## Figma

**File key:** Mr6M1UwQ0i45tEOMHSHe6G

### Page Templates (6)

| Template | Node ID | Shopify Template |
|----------|---------|------------------|
| Homepage (Desktop) | 904:382 | templates/index.json |
| Blog Landing Page | 904:442 | templates/blog.json |
| Blog Detail | 904:467 | templates/article.json |
| Event Type Landing | 912:2416 | templates/page.event-type-landing.json |
| Event Detail | 912:2448 | templates/page.event-detail.json |
| Homepage (Mobile) | 904:1040 | (responsive version of index) |

### Key Components

| Component | Node ID |
|-----------|---------|
| Navigation | 904:688 |
| Footer (Desktop) | 904:359 |
| Footer (Mobile) | 904:1291 |
| Promo Bar | 904:532 |
| Buttons | 904:746 |
| Logo Grid | 904:755 |
| Email Field | 904:1008 |

---

## Design Tokens (Quick Reference)

Full spec: `planning/design-tokens-spec.md` (AUTHORITATIVE)

| Token | Value | Notes |
|-------|-------|-------|
| Primary Blue | #005cba | Nav text, headings, links |
| Secondary Red | #ff595a | Primary button fill, accents |
| Text Blue | #063666 | Body text on light backgrounds |
| Background Taupe | #fdfcf8 | Alternating section bg |
| Heading Font | Geoform Medium 500 | All uppercase, 0.04em tracking |
| Body Font | Zodiak Regular 400 | Sentence case, 15px, 1.5 line height |
| Button Radius | 8px | Also used on cards and form fields |
| Image Radius | 24px | Carousel and hero images |
| Button Height | 40px | 12px/20px padding |
| Promo Bar Height | 40px | 3 color variants |
| Nav Height | 80px | White bg, blue text |

---

## Quote/Estimate Workflow

The existing WooCommerce site uses the WooCommerce Quotation plugin. Key behaviors to replicate:

- Button text: "Add to Estimate" (overridden from "Add to quote" in child theme)
- Products with $0 or empty price show "Request Pricing"
- Quote button hidden on category/collection pages via CSS
- Cart icon hidden via CSS
- 2,281 quote requests in database confirms this is the primary conversion path

### Shopify Implementation

```liquid
{% if product.tags contains 'quote-only' %}
  <!-- Quote app button: "Add to Estimate" -->
  <span class="price--request">Request Pricing</span>
{% else %}
  <!-- Standard Shopify add-to-cart -->
  {{ product.price | money }}
{% endif %}
```

---

## URL Redirect Strategy

| Content | WordPress URL | Shopify URL |
|---------|--------------|-------------|
| Products | /product/{slug}/ | /products/{slug} |
| Categories | /product-category/{slug}/ | /collections/{slug} |
| Blog | /%Y/%m/%d/{slug}/ | /blogs/news/{slug} |
| Pages | /{slug}/ | /pages/{slug} |

Blog posts use date-based WordPress URLs (e.g., /2025/04/19/tent-solutions...) that need redirecting to Shopify's /blogs/news/ pattern.

14 existing redirect rules from the Redirection plugin will be migrated. An additional ~7,000 redirects will be generated from product/category/page/blog URL changes.

---

## Active Plugins (Shopify Equivalents)

| WordPress Plugin | Shopify Replacement |
|-----------------|-------------------|
| WooCommerce | Shopify core |
| WooCommerce Quotation | Quotify or SA Request a Quote |
| Contact Form 7 | Shopify Forms or Klaviyo |
| Ajax Search Lite | Shopify predictive search |
| RevSlider | Custom hero carousel section |
| Instagram Feed | Instafeed app |
| Yoast SEO | Shopify SEO (native) |
| Redirection | Shopify URL Redirects |
| Divi Bars | Custom promo bar section |
| Popup Maker | Privy or native |

---

## Open Blockers

| Blocker | Impact | Status |
|---------|--------|--------|
| Shopify plan tier | Determines available features | Unknown |
| Shopify dev store | Required for any development | Not yet provisioned |
| Font licensing (Geoform + Zodiak) | Required for theme build | Unknown |
| Quote app selection | Core commerce feature | Evaluate after dev store |
| Newsletter platform | Klaviyo vs Mailchimp | TBD |
| DNS access | Required for launch | Unknown |
| Product CSV freshness | Oct 2024 export may be stale | May need re-export |

---

## Time Tracking

Track all work to Harvest, ad-hoc project for Ace Party.

```
Notes format: "Ace + [activity]"

Examples:
  - "Ace + Shopify theme setup"
  - "Ace + Product data migration script"
  - "Ace + Homepage template build"
  - "Ace + QA testing"
```

---

## Agent Guidelines

### Working on Theme Development

1. Work in `theme/` directory (Dawn-based Shopify OS 2.0 theme)
2. Read `planning/design-tokens-spec.md` before styling anything
3. Use CSS custom properties from the design tokens spec
4. Use Liquid for template logic, vanilla JS for interactions
5. All Geoform text must be uppercase
6. Test at 1440px (Figma desktop width) and mobile widths

### Working on Data Migration

1. Read `planning/extraction-summary.md` for source data details
2. Product migration scripts go in `scripts/`
3. Tag products `quote-only` or `has-price` based on price data
4. Non-linen products first (~537), linens consolidated later
5. Matrixify CSV format for Shopify import

### Working on Content Pages

1. Check the relevant Figma node ID (listed above)
2. Use `mcp__claude_ai_Figma__get_design_context` with the file key and node ID
3. Convert Figma output to Shopify Liquid sections
4. Use Shopify section schemas for CMS-editable content
5. Follow Dawn patterns for section structure

---

## Related Files

| File | Purpose |
|------|---------|
| `planning/extraction-summary.md` | Complete WordPress data extraction |
| `planning/design-tokens-spec.md` | AUTHORITATIVE design tokens from Figma |
| Migration plan | `/Users/mlovascio/.claude/plans/happy-conjuring-parasol.md` |
