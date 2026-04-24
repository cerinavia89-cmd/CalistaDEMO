# Calista Landing Page – Changes (Layout/Design Fixes Only)

File modified: `calista_landing.html` (inline CSS)

## 1) Header logo sizing
- Replaced the `header` and `header img` CSS with the provided rules.
- Removed the conflicting duplicate `width` rule so the logo can size correctly via `clamp()`.

## 2) Horizontal overflow fix
- Added global CSS near the top:
  - `html, body { overflow-x: hidden; max-width: 100%; }`
  - `box-sizing: border-box` for all elements
  - global responsive image rule (`img { max-width: 100%; height: auto; }`)
- Replaced `.about .content`, `.about .content .text`, and `.about .content img` with the provided flex rules to prevent the about section from exceeding the viewport.

## 3) Hero image positioning (faces visible) + frosted glass text card
- Repositioned the hero background to keep the people’s faces fully visible:
  - `background-position: center 40%`
- Kept the hero text toward the bottom and on a subtle frosted-glass card (already present in the hero markup).
- Reduced the card footprint slightly (padding + hero text sizes) to minimize any coverage of faces.
- Added `min-height: 680px` on `.hero` to ensure the card sits lower while the faces remain fully visible.

## 4) CSS comment cleanup
- Removed old/conflicting comments inside the header and hero CSS by replacing those blocks.

## 4) Logo image replacement
- Replaced `logo.png` with the provided `CCWorldwide Logo FINAL.png`, cropped to remove excess transparent padding/background.
- Updated `header img` to use `object-fit: contain` so the full logo remains visible (no cropping) while keeping the header height unchanged.

---

## 5) SEO pass — `calista_landing.html`

### `<head>` meta tags
- **`<title>`** updated to: `Calista Consulting Worldwide | Small Business Operations Consulting`
- **`<meta name="description">`** added (155 chars), derived from existing hero/about copy.
- **`<meta name="robots" content="index, follow">`** added.
- **`<link rel="canonical">`** omitted — live domain unknown; add once deployed.

### Open Graph
- Added `og:type`, `og:title`, `og:description`, `og:image` (references `pexels-rdne-7413933.jpg`).
- `og:url` omitted — live domain unknown.

### Twitter Card
- Added `twitter:card=summary_large_image`, `twitter:title`, `twitter:description`, `twitter:image`.

### JSON-LD structured data
- Added `@type: Organization` block with `name`, `logo`, and `email`.
- Address, phone, and social profiles omitted — not available.

### Heading order
- `<h3>Contact Us</h3>` changed to `<h2>` (was skipping a level; no H2 existed in the contact section).
- Matching CSS selector updated from `.contact h3` to `.contact h2`. Visual appearance unchanged.

### Image alt text
- Consultation photo (`pexels-rdne-7413974.jpg`) alt updated from "Consultation meeting" to "Business consultants collaborating with a small business owner".
- Logo alt was already correct (`Calista Consulting Worldwide logo`).

---

## New files

### `robots.txt`
- Allows all crawlers to index all pages.
- Sitemap reference line is included but commented out — uncomment and insert your domain once live.

### `sitemap.xml`
- Lists the single landing page URL.
- Replace `YOURDOMAIN` with your actual domain (e.g. `www.calistaworldwide.com`) before publishing.
- Upload both files to the root of your web server alongside `calista_landing.html`.

---

---

## 6) Mobile responsive pass — `calista_landing.html`

All changes are additive media-query overrides only. No desktop styles were altered.

### Base rules already in place (verified, no changes needed)
- `html, body { overflow-x: hidden; }` ✓
- `*, *::before, *::after { box-sizing: border-box; }` ✓
- `img { max-width: 100%; height: auto; }` ✓
- `<meta name="viewport" content="width=device-width, initial-scale=1.0">` ✓

### Breakpoint: `max-width: 900px`
| Element | Change |
|---|---|
| `.about .content` | `flex-direction: column`, gap reduced to `24px` |
| `.hero` | padding reduced to `80px 16px 40px` |
| `.hero-card h1` | font-size stepped down to `1.9rem` |

### Breakpoint: `max-width: 600px`
| Element | Change |
|---|---|
| `header img` | height capped at `68px` (prevents bulky header on phones) |
| `.hero` | padding `52px 16px 24px`, `min-height: 400px` — keeps card at bottom, faces visible above |
| `.hero-card` | interior padding reduced to `10px 14px` |
| `.hero-card h1` | `1.45rem` |
| `.hero-card p` | `0.95rem` |
| `.about` | padding `36px 16px` |
| `.about h2` | `1.5rem` |
| `.about .content` | gap `18px`, body font `1rem` |
| `.contact` | padding `32px 16px` |
| `.contact a` | `display: inline-block; padding: 8px 0` — meets minimum tap-target height |

### Notes
- No page copy, section order, layout, colours, or images were changed.
- `header img` uses `max-width: 100%` in base styles — this already prevents the `clamp()` minimum (`340px`) from overflowing on narrow viewports; the 600px override only reduces height.
- `min-height` on `.hero` avoids iOS Safari vh trap by using padding-based sizing with a modest fallback floor.

---

## 7) Favicon pass — `calista_landing.html` + new files

### Source image
`CCWorldwide Logo FAVICON.png` (5000×5000 px, RGBA) — resized with Lanczos resampling via Python Pillow.

### New files in `calista_worldwide_final_logo_replaced\`

| File | Size | Purpose |
|---|---|---|
| `favicon.ico` | 16×16, 32×32, 48×48 (multi-size) | Legacy browser tab icon |
| `favicon-16x16.png` | 16×16 | Standard small favicon |
| `favicon-32x32.png` | 32×32 | Standard retina favicon |
| `apple-touch-icon.png` | 180×180 | iOS home screen icon |
| `android-chrome-192x192.png` | 192×192 | Android home screen icon |
| `android-chrome-512x512.png` | 512×512 | Android splash / PWA icon |
| `site.webmanifest` | — | Web app manifest |

### `site.webmanifest` values
- `name` / `short_name`: `Calista Consulting Worldwide`
- `display`: `standalone`
- `theme_color` / `background_color`: `#0f4471` (matches `--primary` CSS variable)

### Tags added to `<head>` of `calista_landing.html`
```html
<link rel="icon" href="favicon.ico" sizes="any">
<link rel="icon" type="image/png" href="favicon-32x32.png" sizes="32x32">
<link rel="icon" type="image/png" href="favicon-16x16.png" sizes="16x16">
<link rel="apple-touch-icon" href="apple-touch-icon.png" sizes="180x180">
<link rel="manifest" href="site.webmanifest">
```

### Notes
- No layout, styling, or copy was changed.
- All files use paths relative to the site root — upload them alongside `calista_landing.html`.
