# TERRIZZI — Band Website

Static website for **Terrizzi**, a four-piece Dutch rock band. Live at [preview.terrizzi.nl](https://preview.terrizzi.nl).

## Pages

| File | Route | Purpose |
|---|---|---|
| `index.html` | `/` | Landing page with hero image and promo video |
| `band.html` | `/band.html` | Band member profiles |
| `media.html` | `/media.html` | Photos and embedded video |
| `live.html` | `/live.html` | Upcoming and past shows |
| `elements.html` | `/elements.html` | HTML5 UP component reference (not linked in nav) |
| `generic.html` | `/generic.html` | HTML5 UP generic page template (not linked in nav) |

## Architecture

The site is a fully static multi-page HTML site — no build step, no framework, no JavaScript bundler.

```
.
├── index.html              # Home
├── band.html               # Band
├── media.html              # Media
├── live.html               # Live
├── CNAME                   # GitHub Pages custom domain
├── assets/
│   ├── css/
│   │   ├── main.css        # HTML5 UP Massively base styles (compiled from sass/)
│   │   ├── terrizzi.css    # Custom overrides and brand styles
│   │   ├── noscript.css    # Fallback styles when JS is disabled
│   │   └── fontawesome-all.min.css
│   ├── sass/               # SCSS source for main.css (not compiled at deploy time)
│   ├── js/                 # jQuery + HTML5 UP interaction scripts
│   ├── img/
│   │   ├── logo/           # Brand logos and icons (PNG/SVG, light and dark variants)
│   │   ├── band/           # Band photos
│   │   └── [member dirs]/  # Per-member photo sets
│   └── webfonts/           # Font Awesome webfonts
└── images/                 # HTML5 UP background images (bg.jpg, overlay.png, pic0x.jpg)
```

### CSS layers

1. **`assets/sass/`** — HTML5 UP Massively SCSS source. The compiled output is `assets/css/main.css`. The SCSS is kept for reference; it is not recompiled during deploy.
2. **`assets/css/terrizzi.css`** — All band-specific customisations: logo layout, hero background switching (9:16 mobile / 16:9 desktop), colour overrides, and social icon sizing.

### JavaScript

No custom JS. The scripts in `assets/js/` are the unmodified HTML5 UP Massively bundle: jQuery, ScrollEx, ScrollY, and utility helpers that handle scroll-triggered class toggling and the mobile nav drawer.

## Deploy — GitHub Pages

The repository deploys automatically to GitHub Pages on every push to `master`. No CI workflow file is required; GitHub Pages is configured to serve directly from the root of the `master` branch.

The `CNAME` file contains `preview.terrizzi.nl`, which tells GitHub Pages to respond on that custom domain. DNS must have a `CNAME` record pointing `preview.terrizzi.nl` → `dvterrizzi.github.io`.

**Deploy flow:**

```
git push origin master
       │
       └─▶ GitHub Pages picks up the push
               └─▶ serves the repo root as static files
                       └─▶ https://preview.terrizzi.nl
```

Because the site is purely static, there is no build phase. Any file pushed to `master` is immediately live (propagation typically takes under a minute).

## Local development

Open any HTML file directly in a browser, or run a local file server to avoid cross-origin issues with relative paths:

Preferably, use VS Code with the Live Server extension. Or otherwise:

```bash
# Python 3
python3 -m http.server 8080
```

Then open `http://localhost:8080`.

## Attribution

Base theme: [Massively by HTML5 UP](https://html5up.net) — licensed under [Creative Commons Attribution 3.0](https://creativecommons.org/licenses/by/3.0/). Custom styles and all band content © Terrizzi.
