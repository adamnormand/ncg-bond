# ncg-bond — thebondpub.ca

Static rebuild of **thebondpub.ca** (formerly WordPress + Bridge theme + LayerSlider), hosted on GitHub Pages.
Plain HTML/CSS, no JavaScript, no build step. Migrated 2026-09-28.

## Structure

| Path | Page |
|---|---|
| `index.html` | Home (CSS crossfade hero + tile grid) |
| `reservations/` | Reservations |
| `menu/` | Menu (CSS tabs: Drinks, Brunch, Lunch, Dinner, Happy-Hour, Late Night) |
| `menu/lunch-dinner/`, `menu/brunch/`, `menu/drinks/` | Menu sub-pages |
| `delivery/` | Uber Eats / DoorDash ordering |
| `experience/` + `pool/`, `karaoke/`, `sports/` | Experience pages |
| `events/` | Events (points to Facebook) |
| `contact/` | Address, hours, Google Map embed |
| `404.html` | Not-found page |
| `assets/site.css` | All styles |
| `assets/img/` | Images (large PNGs re-encoded to JPEG/WebP) |
| `assets/menu/` | Menu pages rendered from the original PDFs (WebP, 1100 px wide) |
| `CNAME`, `.nojekyll`, `favicon.*`, `apple-touch-icon.png` | Pages config and icons |

URLs match the WordPress permalinks, so existing links and search results keep working.
All internal links are relative, so the site also previews correctly at `https://<user>.github.io/ncg-bond/`
(except `404.html`, which uses root paths and only works on the custom domain).

Fonts: Google Fonts (Raleway, Viga, Orbitron, Acme). Third-party calls: Google Fonts, the Google Maps iframe on Contact.

## Editing

- Text lives directly in each `index.html`. Header, nav and footer are repeated in every page — change all of them together.
- To update a menu, replace the WebP files in `assets/menu/` (same names), or add pages and extend the `<div class="menu-pages">` blocks.

## Publishing

1. Settings → Pages → Build and deployment → **Deploy from a branch** → `main` / `/ (root)`.
2. Custom domain: `thebondpub.ca` (already in `CNAME`). Tick **Enforce HTTPS** once the certificate is issued.

## DNS (at the registrar — do this after Pages is live)

```
@    A     185.199.108.153
@    A     185.199.109.153
@    A     185.199.110.153
@    A     185.199.111.153
@    AAAA  2606:50c0:8000::153
@    AAAA  2606:50c0:8001::153
@    AAAA  2606:50c0:8002::153
@    AAAA  2606:50c0:8003::153
www  CNAME <github-user>.github.io
```

Remove any other A/AAAA/CNAME records on `@` and `www` that point to the old host. Leave MX, TXT/SPF, DKIM and SRV records alone.
