# SBIHM Hotel Management Landing Page
**Developed by Plan D Media for Subhas Bose Institute of Hotel Management (SBIHM), Kolkata**
**Build: 2026 Admissions Season | Course: Bachelor of Hotel Management (BHM)**

---

## Quick Start

Open `index.html` in a browser. No build step needed — pure HTML/CSS/JS.

For local development with a live-reload server:
```bash
npx serve .
# or
python -m http.server 8000
```

For production: minify CSS and JS (see Production section below).

---

## Files

```
/
├── index.html          Main landing page (all 15 sections)
├── styles.css          All styles — mobile-first, CSS custom properties
├── script.js           Vanilla JS — 12 interactive modules
├── README.md           This file
└── assets/
    ├── sbihm-logo.png              ← REPLACE: Place actual logo here
    ├── hero-student.jpg            ← REPLACE: Real SBIHM student photo
    ├── hero-student.webp           ← REPLACE: WebP version of hero photo
    ├── sbihm-bhm-brochure.pdf      ← REPLACE: Final brochure PDF
    ├── og-bhm-2026.jpg             ← REPLACE: Open Graph social share image (1200×630)
    ├── campus/
    │   ├── training-kitchen.jpg    ← REPLACE: Training kitchen photo
    │   ├── training-kitchen.webp
    │   ├── front-office.jpg        ← REPLACE: Mock front office photo
    │   ├── front-office.webp
    │   ├── restaurant-lab.jpg      ← REPLACE: Mock restaurant lab photo
    │   ├── restaurant-lab.webp
    │   ├── housekeeping-lab.jpg    ← REPLACE: Housekeeping lab photo
    │   ├── housekeeping-lab.webp
    │   ├── bakery-lab.jpg          ← REPLACE: Bakery lab photo
    │   └── bakery-lab.webp
    └── partners/
        └── [hotel logos]           ← REPLACE: Licensed partner logos
                                       (Taj, ITC, JW Marriott, Hyatt, Oberoi,
                                        Hilton, Marriott, Radisson, Lalit, Leela,
                                        Hard Rock, Park, Vivanta, Ginger, Holiday Inn,
                                        Sayaji, Pride, Crowne Plaza, Royal Caribbean,
                                        Carnival, Apollo, Fortis, IndiGo, Akasa)
```

---

## Items to Confirm with Client BEFORE Launch

| # | Item | Status |
|---|------|--------|
| 1 | **Exact fee structure** — Year 1 tuition, admission fee, uniform/kit, industrial training fee, hostel | ⚠️ PLACEHOLDER in fees table |
| 2 | **Real student photos** — hero, testimonial avatars, campus labs | ⚠️ PLACEHOLDER paths |
| 3 | **Final brochure PDF** — `assets/sbihm-bhm-brochure.pdf` | ⚠️ PLACEHOLDER |
| 4 | **Barasat campus address** — full postal address | ⚠️ PLACEHOLDER in campus section and footer |
| 5 | **Branded email setup** — confirm `admissions@sbihm.in` and `info@sbihm.in` are live | ⚠️ Placeholder used throughout |
| 6 | **Partner hotel logos** — must have licensed/permitted copies | ⚠️ Text fallbacks in use |
| 7 | **GTM container ID** — from Plan D Media's GTM account | ⚠️ Commented out in `<head>` |
| 8 | **Meta Pixel ID** — from Plan D Media's Ads Manager | ⚠️ Commented out in `<head>` |
| 9 | **Google Ads conversion tag ID** | ⚠️ Commented out in `<head>` |
| 10 | **Lead endpoint** — LeadSquared / ExtraaEdge CRM webhook URL | ⚠️ `console.log` only; see script.js |
| 11 | **Canonical domain** — confirm if `sbihm.in/hotel-management/` is correct | ⚠️ Used in `<link rel="canonical">` and schema |
| 12 | **Social media handles** — confirm Facebook, Instagram, LinkedIn, YouTube URLs are current | ⚠️ Using known URLs |
| 13 | **OG image** — `assets/og-bhm-2026.jpg` (1200×630px) for social sharing | ⚠️ PLACEHOLDER |

---

## Integrations Required Before Go-Live

### 1. Google Tag Manager
Find in `index.html`:
```html
<!-- Google Tag Manager - PASTE GTM ID FROM PLAN D BEFORE GO-LIVE -->
```
Uncomment and replace `GTM-XXXXXXX` with actual GTM container ID.
Also uncomment the `<noscript>` iframe in `<body>`.

### 2. Meta Pixel
Find and uncomment the Meta Pixel snippet. Replace with actual Pixel ID.

### 3. Google Ads Conversion Tracking
Uncomment the gtag snippet. Replace with actual Conversion ID.

### 4. Lead Form Endpoint
In `script.js`, find:
```javascript
// TODO: Replace with real endpoint — integrate with LeadSquared / ExtraaEdge / WhatsApp API
```
Replace the simulated `await new Promise(...)` block with a real `fetch()` POST to the CRM webhook.

**LeadSquared example:**
```javascript
const res = await fetch('https://api.leadsquared.com/v2/LeadManagement.svc/Lead.Capture?accessKey=...', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify([
    { Attribute: 'FirstName', Value: formData.name },
    { Attribute: 'Mobile',    Value: formData.phone },
    { Attribute: 'EmailAddress', Value: formData.email },
    // ... more fields
  ])
});
```

### 5. WhatsApp Auto-Reply (Optional)
The WhatsApp links use `wa.me` — pre-filled message is already set. For automated responses, integrate a WhatsApp Business API (Interakt, Wati, or AiSensy).

---

## Brochure PDF Setup

1. Place the final brochure PDF at `assets/sbihm-bhm-brochure.pdf`
2. The download is triggered by the brochure modal form submission in `script.js`
3. A lead is captured before the download triggers — confirm CRM integration is live

---

## Performance Notes

- Target: Lighthouse Mobile Performance ≥ 90
- Hero image must be optimized: **WebP + JPG fallback, compressed to ≤ 150KB**
- All campus images: **WebP + JPG, compressed to ≤ 80KB each**
- Fonts are preconnected in `<head>` for faster loading
- Images below the fold use `loading="lazy"`
- JS is deferred with `defer` attribute

**Recommended tools:**
- Image compression: Squoosh (squoosh.app) — export WebP at ~80% quality
- CSS/JS minification: `csso styles.css -o styles.min.css` and `terser script.js -o script.min.js`
- Once minified, update `index.html` to reference `.min.css` and `.min.js`

---

## SEO Checklist

- [x] Single H1 — only in hero section
- [x] `<title>` and `<meta description>` set
- [x] `<link rel="canonical">` — confirm URL before launch
- [x] Open Graph tags set
- [x] Twitter card set
- [x] FAQPage JSON-LD schema — 10 items
- [x] CollegeOrUniversity JSON-LD schema
- [x] Course JSON-LD schema
- [x] All images have descriptive `alt` text
- [ ] Submit sitemap to Google Search Console after launch
- [ ] Verify schema at search.google.com/test/rich-results

---

## Accessibility Checklist

- [x] `<main>` with `id="main-content"` and skip link
- [x] Semantic HTML5 structure
- [x] All interactive elements keyboard-navigable
- [x] ARIA attributes on accordion, carousel, drawer, modals
- [x] Focus rings on all interactive elements (gold outline)
- [x] `prefers-reduced-motion` disables animations
- [x] Form labels associated with inputs (not just placeholder)
- [x] Error messages use `role="alert"` + `aria-live="polite"`
- [x] Colour contrast: red on cream ✓, gold on black ✓, white on red ✓

---

## Browser Support

- Chrome 90+, Firefox 88+, Safari 14+, Edge 90+
- iOS Safari 14+, Android Chrome 90+
- No IE11 support (acceptable for this target audience)

---

## Known Limitations / What's Not Yet Wired Up

1. **Form submissions** go to `console.log` — CRM integration is required
2. **Brochure PDF** download will 404 until the actual file is placed in `assets/`
3. **Partner logos** show text fallbacks — replace with licensed logo image files
4. **Campus images** show CSS gradient placeholders — replace with real photography
5. **Hero student photo** uses a CSS gradient background — replace immediately before launch

---

## Contact

**Plan D Media** | teamplandmedia@gmail.com
Client: SBIHM — admissions@sbihm.in | +91 98300 12536
