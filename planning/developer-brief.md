# Ace Party & Tent Rental - Developer Brief

> **Start here.** This is the single entry point for anyone working on this project.
> **Last Updated:** 2026-03-03

---

# What is this project?

Ace Party & Tent Rental is migrating from WordPress/WooCommerce to Shopify. The new site is built on a Dawn v15.4.1 child theme with custom CSS overrides and custom Liquid sections matching Figma designs.

- **Client:** Ace Party & Tent Rental (Gandel family)
- **Account:** Learned Media (LRND) - direct client
- **Current site:** https://acepartyrental.com (WordPress/WooCommerce, Divi, WPEngine)
- **Shopify store:** acepartyrental.myshopify.com
- **GitHub repo:** github.com/mlovascio/lrnd-ace-shopify
- **Figma:** File key Mr6M1UwQ0i45tEOMHSHe6G

---

# Tech Stack

- **Platform:** Shopify Online Store 2.0
- **Base theme:** Dawn v15.4.1
- **Templates:** JSON-based section architecture
- **CSS:** Custom ace-*.css files layered after Dawn base styles. No Dawn core edits.
- **JS:** Vanilla JavaScript only. No frameworks, no build tools.
- **Fonts:** Zodiak (Fontshare CDN), Geoform (pending .woff2, Montserrat fallback)

---

# Dev Environment

```bash
# Clone and navigate
git clone git@github.com:mlovascio/lrnd-ace-shopify.git
cd lrnd-ace-shopify

# Start dev server (requires Shopify CLI)
cd theme/
shopify theme dev --store acepartyrental.myshopify.com

# Dev server runs at http://127.0.0.1:9292
# For remote access: shopify theme dev --store acepartyrental.myshopify.com --host 0.0.0.0
```

Git push does NOT deploy to Shopify. The store is updated separately.

---

# Brand Overview

## Colors
- Primary Blue: #005cba (nav, headings, links)
- Secondary Red: #ff595a (buttons, CTAs)
- Text Blue: #063666 (body text)
- Background Taupe: #fdfcf8 (alternating sections)
- Footer Gradient: linear-gradient(to right, #0c6bcd, #387fd7)

## Typography
- **Headings:** Geoform Medium 500, ALWAYS uppercase, letter-spacing 0.04-0.06em
- **Body:** Zodiak Regular 400, sentence case, 15px, 1.5 line-height
- **Buttons/CTAs:** Geoform Medium, 12px, uppercase, 0.04em tracking

## Key Dimensions
- Page width: 1440px (1400px Shopify setting)
- Content max-width: ~1232px (104px padding each side)
- Button radius: 8px
- Image radius: 24px
- Button height: 40px

Full spec: `planning/design-tokens-spec.md` (428 lines, AUTHORITATIVE)

---

# Architecture Pattern

All customization follows the same pattern:

1. Dawn provides the base Liquid markup and functionality
2. Custom `ace-*.css` files override Dawn's styles to match Figma
3. Custom `ace-*.liquid` sections add new components not in Dawn
4. Custom `ace-*.js` files add interactive behavior (carousels, tabs)

**Never edit Dawn core files.** If Dawn handles something (dropdowns, mobile drawer, cart, search), override with CSS. Only create new Liquid when Dawn has no equivalent.

---

# Current File Structure

```
theme/
  assets/
    ace-brand.css          # Brand tokens, typography, button variants (274 lines)
    ace-header.css         # Header + promo bar overrides (161 lines)
    ace-footer.css         # Footer gradient + layout overrides (217 lines)
    mask-blobs.css         # Dawn's 6 blob mask shapes (built-in)
  snippets/
    ace-fonts.liquid       # Zodiak CDN + Geoform placeholder
  sections/
    header.liquid          # Dawn header (modified: includes ace-header.css)
    footer.liquid          # Dawn footer (modified: includes ace-footer.css)
  config/
    settings_data.json     # 5 Ace color schemes configured
  layout/
    theme.liquid           # Modified: includes ace-fonts + ace-brand.css
```

---

# What's Built (Phase 1 Complete)

- [x] Shopify dev store provisioned and authenticated
- [x] Dawn v15.4.1 cloned, committed, pushed
- [x] Design tokens extracted from Figma, CSS custom properties defined
- [x] Zodiak font loading from Fontshare CDN
- [x] 5 color schemes in settings_data.json
- [x] Header styled (promo bar, nav, dropdowns, mobile drawer, sticky)
- [x] Footer styled (gradient bg, newsletter, links, social, mobile)

---

# What's Next (Phase 2: Homepage Sections)

7 custom Shopify sections to build, each with its own Liquid, CSS, and optionally JS:

| # | Section | Key Feature | Ticket |
|---|---------|-------------|--------|
| 04 | Hero Carousel | Blob-masked images, overlay text, auto-advance | 04-hero-carousel.md |
| 05 | Logo Grid | Client logos at 30% opacity, crossfade animation | 05-logo-grid.md |
| 06 | Two-Up Services | Two square images with blob masks and CTA buttons | 06-two-up-services.md |
| 07 | Event Cards | 4-card grid with frosted-glass icon badges | 07-event-cards.md |
| 08 | Tabbed Content | Sidebar tabs with image panels, 30%/100% opacity | 08-tabbed-content.md |
| 09 | Testimonials + CTA | 100px headline, 3-card carousel, quote CTA | 09-testimonials-cta.md |
| 10 | Feature/Blog Card | Horizontal card with image + content | 10-feature-blog.md |

After building all 7: assemble into `templates/index.json` (ticket #11).

---

# Blob Mask Strategy

Dawn includes 6 organic blob shapes in `assets/mask-blobs.css` as CSS custom properties:
- `--shape--blob-1` through `--shape--blob-6`

Use these with `clip-path: polygon(var(--shape--blob-N))` on image containers. Test each shape against the Figma designs to find the best matches. Different sections may use different blob variants.

---

# Quote/Cart Hybrid

93% of products are quote-only (no price). The site uses a hybrid workflow:

- Products tagged `quote-only`: Show "Add to Estimate" and "Request Pricing"
- Products tagged `has-price`: Show standard "Add to Cart" with price

A quote app (Quotify, SA Request a Quote, etc.) will handle the estimate submission. App selection is pending - build product pages with conditional Liquid logic first.

---

# Key Reference Files

| File | What It Contains |
|------|-----------------|
| `planning/design-tokens-spec.md` | AUTHORITATIVE design token values (colors, fonts, spacing, components) |
| `planning/content-reference.md` | Homepage content from current site (slides, testimonials, logos, etc.) |
| `planning/nav-menu-structure.md` | Full navigation tree (primary, utility, footer) |
| `planning/icon-inventory.md` | All icons and assets needed, with library recommendations |
| `planning/extraction-summary.md` | WordPress data overview (6,735 products, 296 posts, etc.) |
| `planning/tickets/asana/00-README.md` | Ticket index (23 tickets across 6 phases) |

---

# Conventions

- **CSS files:** Named `ace-{component}.css`, loaded by the corresponding section via `{{ 'ace-{component}.css' | asset_url | stylesheet_tag }}`
- **Sections:** Named `ace-{component}.liquid` for custom sections
- **Snippets:** Named `ace-{component}.liquid` for reusable partials
- **CSS variables:** Prefixed `--ace-` (defined in ace-brand.css)
- **Commit messages:** Conventional commits (`feat:`, `fix:`, `docs:`, `style:`)

---

# Constraints

- **No Dawn core edits.** Override with CSS, add new sections/snippets.
- **No build tools.** Plain CSS and vanilla JS only.
- **No HubL.** This is Shopify/Liquid, not HubSpot.
- **Git is not deployment.** Push to GitHub freely; Shopify store updates separately.
- **Geoform font is placeholder.** Using Montserrat fallback until .woff2 files arrive from designer.
- **Local dev only.** Test via `shopify theme dev`, not on the live store.
