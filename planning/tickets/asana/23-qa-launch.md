# ACE: QA and Launch Prep

**Classification:** Finalization
**Dependencies:** All other tickets

---

# Deliverable

Comprehensive QA testing across all templates, performance optimization, cross-browser testing, and launch execution plan.

---

# QA Checklist

## Visual Fidelity
- [ ] Homepage: all 7 sections match Figma at 1440px and 375px
- [ ] Blog landing: 3-column grid, pagination, hero
- [ ] Blog article: breadcrumbs, featured image, body text, related posts
- [ ] Event type landing: 4-column grid, 12 event cards
- [ ] Event detail: hero, gallery, partner logos
- [ ] Product page: quote vs cart mode, images, descriptions
- [ ] Collection page: grid layout, filtering, pagination
- [ ] Cart: drawer opens, line items display, estimate terminology

## Typography
- [ ] Geoform loads (or Montserrat fallback renders acceptably)
- [ ] Zodiak loads from Fontshare CDN
- [ ] All heading levels use correct Geoform size and weight
- [ ] Body text uses Zodiak 15px with 1.5 line-height
- [ ] Button text uses CTA style (12px uppercase)

## Responsive
- [ ] All pages tested at 375px (mobile)
- [ ] All pages tested at 768px (tablet)
- [ ] All pages tested at 1440px (desktop)
- [ ] No horizontal scroll on any viewport
- [ ] Touch targets minimum 44px on mobile

## Performance
- [ ] Lighthouse Performance > 90 on mobile for homepage
- [ ] LCP < 2.5s (hero image)
- [ ] CLS < 0.1
- [ ] FID/INP < 200ms
- [ ] Total page weight < 2MB
- [ ] All below-fold images lazy loaded
- [ ] No render-blocking resources

## Functionality
- [ ] Hero carousel auto-advances and pauses
- [ ] Tab navigation works (40+ Years section)
- [ ] Testimonial carousel slides and swipes
- [ ] Logo grid animation runs
- [ ] All buttons link to correct pages
- [ ] Product add-to-cart works (priced items)
- [ ] Product add-to-estimate works (quote items)
- [ ] Cart drawer opens and displays items
- [ ] Search returns relevant results
- [ ] Newsletter signup submits

## SEO
- [ ] All pages have unique title tags
- [ ] All pages have meta descriptions
- [ ] Sitemap accessible at /sitemap.xml
- [ ] Robots.txt is correct
- [ ] Canonical URLs are set
- [ ] Structured data (JSON-LD) for organization, products
- [ ] 100 redirects spot-checked (301 responses)

## Cross-Browser
- [ ] Chrome (latest)
- [ ] Safari (latest)
- [ ] Firefox (latest)
- [ ] Mobile Safari (iOS)
- [ ] Mobile Chrome (Android)

## Accessibility
- [ ] Keyboard navigation works site-wide
- [ ] Focus states visible on all interactive elements
- [ ] Images have alt text
- [ ] Color contrast meets WCAG AA (4.5:1 body, 3:1 large text)
- [ ] Carousels have pause controls
- [ ] Forms have proper labels

---

# Launch Sequence

## T-7 Days
- [ ] Content freeze on WordPress (no new blog posts or product changes)
- [ ] Final product data export and import if needed
- [ ] Full QA pass on dev store

## T-3 Days
- [ ] DNS TTL reduction (set to 300s / 5 min)
- [ ] Final redirect validation
- [ ] Backup current WordPress site

## Launch Day (T-0)
- [ ] DNS cutover to Shopify
- [ ] SSL certificate verification
- [ ] Sitemap submission to Google Search Console
- [ ] GA4 tracking verification
- [ ] Smoke test: homepage, 5 products, 3 blog posts, cart flow
- [ ] Monitor for 404 errors

## T+1 Day
- [ ] Check Google Search Console for crawl errors
- [ ] Verify analytics data flowing
- [ ] Test 50 redirects from external links / search results

## T+7 Days
- [ ] Redirect validation (check for 404 spikes)
- [ ] Analytics comparison (traffic, bounce rate, conversions)
- [ ] Address any reported issues

## T+30 Days
- [ ] SEO performance review (rankings, traffic)
- [ ] User feedback collection
- [ ] Phase 2 planning (linen product consolidation, additional features)

---

# Acceptance Criteria

- [ ] All QA checklist items pass
- [ ] Cross-browser testing complete, no critical issues
- [ ] Lighthouse mobile performance > 90
- [ ] Launch sequence documented and approved by LRND
- [ ] DNS cutover executed successfully
- [ ] No critical 404s or broken functionality post-launch
- [ ] GA4 tracking confirmed working

---

# Reference Docs

- `planning/design-tokens-spec.md` - Visual reference for QA
- All section tickets (#04-#10) for individual component specs
- Figma file: Mr6M1UwQ0i45tEOMHSHe6G (visual reference)
- Current site: https://acepartyrental.com (comparison reference)
