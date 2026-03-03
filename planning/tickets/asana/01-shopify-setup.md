# ACE: Shopify Store Setup and Theme Config

**Classification:** Foundation
**Dependencies:** None
**Status:** COMPLETE

---

# Deliverables

Set up Shopify development environment and initialize Dawn theme:

- Shopify Partner development store provisioned (acepartyrental.myshopify.com)
- Shopify CLI installed and authenticated
- Dawn v15.4.1 theme cloned into `theme/` directory
- Repository created on GitHub (lrnd-ace-shopify)
- CLAUDE.md with project context
- `planning/` directory with migration docs, design tokens spec, extraction summary
- Dev server confirmed working (`shopify theme dev`)

---

# Technical Notes

- Dawn v15.4.1 is the base (Shopify Online Store 2.0, JSON templates, section architecture)
- All customization is additive: custom CSS override files, not Dawn core edits
- Dev server runs locally only - Git is the deployment bridge to Shopify
- Theme dev server: `shopify theme dev --store acepartyrental.myshopify.com`

---

# Files Created

- `CLAUDE.md` - Agent context and project instructions
- `planning/design-tokens-spec.md` - Authoritative design token spec from Figma
- `planning/extraction-summary.md` - WordPress/WooCommerce extraction overview
- `planning/data-migration/` - Migration scripts directory
- `planning/tickets/asana/` - This ticket set

---

# Acceptance Criteria

- [x] Shopify dev store provisioned and accessible
- [x] Shopify CLI installed and authenticated
- [x] Dawn theme cloned and committed
- [x] Dev server starts without errors
- [x] Repository pushed to GitHub
- [x] CLAUDE.md written with full project context

---

*Completed: 2026-03-02*
