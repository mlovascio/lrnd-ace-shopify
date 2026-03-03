# Ace Party - Icon and Asset Inventory

> **Source:** Figma file Mr6M1UwQ0i45tEOMHSHe6G (extracted 2026-03-03)
> **Purpose:** Asset checklist for Shopify theme build

---

# Event Category Icons

Used in the "Our Events" section (#07). Each icon sits inside a 44x44px frosted-glass badge.

**Badge specs:**
- Size: 44x44px
- Background: rgba(0, 0, 0, 0.1)
- Backdrop blur: 20px
- Border radius: 22px (circle)
- Padding: 14px (icon renders at 16x16px)

| Icon | Figma Node | Description | Icon Library Match |
|------|-----------|-------------|-------------------|
| Corporate | 904:977 | Building/office facade, 2-story with tower wing | Phosphor "BuildingOffice", Lucide "building-2" |
| Weddings | 904:979 | Diamond/gem viewed from above with facets | Phosphor "Diamond", Lucide "diamond" |
| Film | 904:981 | Movie clapperboard with hinged top | Phosphor "Clapperboard", Lucide "clapperboard" |
| Educational | 904:983 | Graduation cap with tassel | Phosphor "GraduationCap", Lucide "graduation-cap" |

All icons: white fill, 16x16px, `var(--fill-0, white)`

**Recommendation:** The Figma icons are custom enough to warrant exporting directly from Figma as SVGs rather than substituting from an icon library.

---

# Utility Icons

| Icon | Description | Size | Color | Usage |
|------|-------------|------|-------|-------|
| Caret Down | Chevron V-shape | 16x16px (11x6 vector) | #005CBA | Nav dropdown indicators |
| Caret Right | Same chevron rotated | 16x16px (11x6 vector) | #005CBA | Event card "go to" indicator |
| Close X | Two diagonal crossing lines | 16x16px (10x10 vector) | Varies by promo variant | Promo bar dismiss button |
| Newsletter Arrow | Same as caret right | 16x16px | White | Footer email field submit |

**Recommendation:** Source from any standard icon library (Phosphor, Lucide, Heroicons). Dawn already includes caret, close, and arrow icons in its SVG assets.

---

# Social Icons

| Icon | Figma Node | Size | Color | Usage |
|------|-----------|------|-------|-------|
| Instagram | 904:374 | 16x16px | White | Footer |
| Facebook | 904:375 | 16x16px | White | Footer |

**Note:** Dawn already has Instagram and Facebook SVG icons in theme assets (`icon-instagram.svg`, `icon-facebook.svg`). The footer social links section (`social-icons.liquid`) renders these automatically when social URLs are configured in settings.

---

# Brand Assets

| Asset | Figma Node | Size | Notes |
|-------|-----------|------|-------|
| Ace Logo (wordmark) | 904:638 | 183x31px | Tent/party hat mark + "ACE PARTY & TENT RENTAL" text. Must export from Figma. Two versions needed: blue (#005CBA) for header, white for footer |

**Action:** Export logo from Figma in SVG format. Upload to Shopify at Settings > Files, then reference in theme customizer.

---

# Blob Mask Shapes

Dawn v15.4.1 ships with 6 blob mask shapes in `assets/mask-blobs.css`:
- `--shape--blob-1` through `--shape--blob-6`

These are CSS `clip-path: polygon()` values that create organic, rounded shapes. The Figma designs use organic blob shapes on hero images, two-up service images, and event cards.

**Strategy:** Use Dawn's built-in blob shapes via `clip-path: polygon(var(--shape--blob-N))`. Test each of the 6 shapes against the Figma designs to find the closest matches. May need different shapes for different sections.

Dawn also includes an arch mask via `mask-arch.svg` with clipPath ID `Shape-Arch`.

---

# Client Logos

10 logos needed for the Logo Grid section (#05):
- NYU
- Columbia University
- NYSE
- Lionel Richie
- Apple
- NBC Universal
- Twitter
- Central Park Conservancy
- Viacom
- NYC Office of the Mayor

**Action:** Request logo files from client, or export from Figma. Logos display at 30% opacity with grayscale filter, so exact color fidelity is not critical. SVG preferred, PNG acceptable.

---

# Asset Export Checklist

- [ ] Ace logo (SVG, blue version for header)
- [ ] Ace logo (SVG, white version for footer)
- [ ] 4 event category icons (SVG, white)
- [ ] 10 client logos (SVG or PNG, any color)
- [ ] Hero carousel background images (JPG, 1440x670px minimum)
- [ ] Two-up service images (JPG, 1136x1136px for 2x retina)
- [ ] Event card images (JPG, 536x536px for 2x retina)
- [ ] Tabbed content images (JPG, various sizes)

**Priority:** Logo and category icons are needed first (blocks #04-#07). Client logos and photos can come later during content population.
