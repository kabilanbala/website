# CBSG Electromechanical Works LLC: One-Page Website

A static one-page corporate website. All HTML, CSS and JavaScript live in `src/index.html`; `src/assets/` holds images only. There is no build step, framework, backend or third-party script.

## File structure

```
.claude/launch.json     local preview server config (optional)
README.md
src/
├── index.html          markup, styles (design tokens at top of <style>), script, SEO meta, JSON-LD
└── assets/
    ├── logo-96.webp, logo-192.webp/.png, logo-512.png   official logo, circle-cropped
    ├── hero-900/1600/2000.webp                    hero photograph
    ├── vision-900.webp, vision-1600.webp                vision & mission background
    ├── about.webp
    ├── fonts/Oswald-Variable.woff2                      self-hosted title and button font (SIL OFL, Latin subset)
    └── services/*.webp                                  11 service images
```

## Local development

```bash
python3 -m http.server 5173 --directory src
```

Open http://localhost:5173. Any static server works. Do not open `index.html` via `file://` in some previews, as relative images may not load.

## Production build

None. Deploy the contents of `src/` as the site root.

## Configuration and external services

None required: no environment variables, API keys or backend.

- **Quotation enquiries** use a `mailto:info@cbsgroup.ae` link with a prefilled subject and body (contact section). Header, menu and hero buttons scroll to that section. To add a real form later, use a provider such as Formspree or Netlify Forms and replace the mailto button.
- **Canonical URL, Open Graph and JSON-LD** assume `https://www.cbsgroup.ae/`. Change them in `<head>` if the live domain differs. `og:image` points to `assets/logo-512.png` on that domain.
- **Contact details** (phone, email, P.O. Box, website) appear in the contact card, footer and JSON-LD. Update all three together.
- **Design tokens** (colours, type scale, spacing, breakpoints) are documented at the top of the `<style>` block. Content max width is `--container: 1440px`. Titles and button text use Oswald (`--font-display`); body text uses the system font stack unless Inter/Manrope are installed.

## Hosting and domain

Any static host works (Netlify, Cloudflare Pages, GitHub Pages, cPanel).

1. Upload `src/` as the site root (or connect the repo and set the publish directory to `src`).
2. Add the custom domain in the host's dashboard and set DNS as the host instructs (typically a CNAME for `www` plus the host's apex records).
3. Enable HTTPS and redirect the apex domain to `www` so it matches the canonical URL.

## Image sources

- Hero (`hero-*.webp`): Unsplash photo `Fr6zexbmjmc` (Dubai skyline).
- Vision & mission (`vision-*.webp`): Unsplash photo `gKMxcHB3U3E` (glass facade at sunset).
- `services/painting.webp`: Unsplash image `photo-1562259949-e8e7689d7828` (paint roller).
- `services/cladding.webp`: Unsplash photo `J4Ticm2cX34` (timber slat wall).
- Other service images and `about.webp`: from the CBSG company profile PDF.
- Unsplash images need no attribution but are stock; never present them as completed CBSG projects.

## Known limitations and recommended follow-ups

- The MEP image (from the PDF) is about 400 px wide and looks soft on large screens.
- Replace stock imagery with CBSG's own project photographs when available.
- Content to confirm with CBSG: the trade license lists activities that do not obviously include steel fabrication, pavers/interlock, cladding or cleaning. The website makes no license or certification claims.
- `robots.txt` and `sitemap.xml` are not included (all code is kept in `index.html`); add them at deployment if wanted.

## Verification performed

Browser checks at 320, 375, 768, 1000, 1440 and 1920 px: no horizontal overflow, no console errors, all anchors resolve, mobile menu opens and closes (button, Escape, link click), visible keyboard focus, 11 service cards render, all images load with dimensions and alt text, colour contrast measured at 4.5:1 or better for text, telephone and mailto links correct, no third-party requests.

Not tested: Lighthouse, an HTML validator, screen readers, real devices and Safari, opening the mailto link in a mail client, and the reduced-motion setting.
