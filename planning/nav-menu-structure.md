# Ace Party - Navigation Menu Structure

> **Source:** https://acepartyrental.com (scraped 2026-03-03)
> **Purpose:** Menu structure for Shopify navigation setup
> **Shopify menus:** Online Store > Navigation > Menus

---

# Primary Navigation

## Rental Catalog
- Chairs
  - Chiavari Chairs
  - Folding Chairs
  - Crossback Chairs
  - Ghost Chairs
  - Stacking Chairs
- Tables
  - Round Tables
  - Rectangle/Banquet Tables
  - Cocktail Tables
  - Conference Tables
- Tents
- Catering & Bar
  - Catering Equipment
  - Bar Equipment
  - Beverage Service
  - Food Display
- Chafers & Serving Equipment
- Coffee Makers
- Crowd Control
- Linens
- Tabletop
  - China/Dinnerware
  - Flatware
  - Glassware
  - Charger Plates
- Tent Options
- Conference
- Concessions

## Event Type
- Corporate
- Education
- Weddings
- Private Events
- Festivals
- Film Production & Premieres
- Concerts
- Community Events
- Groundbreaking Ceremonies
- Healthcare
- Trade Shows
- Disaster Relief
- Social Distancing Solutions

## Services
- Tent Services
- Event Services

## About Us

## Contact

---

# Utility Navigation (Secondary)

- Quote List (cart/estimate page)
- Resources (blog)
- Careers (job listings)

---

# Desktop Navigation (Right Side)

- Search (text link, not icon)
- Account (text link, not icon)
- Cart (0) (text link with count)

**Note:** Figma designs show these as text links (Geoform 12px uppercase), not icons. The current site also uses text.

---

# Footer Navigation

- Rental Catalog
- Event Type
- Careers
- Contact
- Tents
- Services
- About
- Resources

---

# Shopify Menu Setup

## main-menu (Primary)
Map the primary nav above to Shopify's nested menu structure. Shopify supports 3 levels of nesting for dropdown menus.

**Note on Rental Catalog:** These categories will become Shopify collections. The dropdown links should point to `/collections/{handle}`.

**Note on Event Type:** These will be Shopify pages using the event-detail template. Links point to `/pages/{handle}`.

## footer (Footer Links)
Single-level menu with the 8 footer links listed above.

---

# Menu Changes for New Site

Consider these updates when building the Shopify menus:
- "Social Distancing Solutions" - consider removing or archiving
- "Quote List" becomes "Your Estimate" per new terminology
- "Resources" maps to Shopify blog at /blogs/news
- Product category links change from /product-category/ to /collections/
- Event type links change from /event-type/ to /pages/
