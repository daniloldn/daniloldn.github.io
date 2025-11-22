## Quick orientation

This repository is a static personal portfolio site (HTML/CSS/JS) built from the "Strata" HTML5 UP template.
Key directories:
- `index.html`, `dissertation.html`, `about.html` — site pages (index is homepage with portfolio gallery).
- `assets/sass/` — Sass source (edit here). Notable files: `main.scss`, `libs/_vars.scss`, `libs/_mixins.scss`.
- `assets/css/main.css` — compiled CSS (do not edit directly; regenerate from Sass).
- `assets/js/main.js` — custom JS behavior; vendor libs stored as `*.min.js` (don't edit those).
- `assets/docs/` — for PDFs like dissertation; `dissertation.html` embeds `assets/docs/dissertation.pdf`.
- `images/thumbs/` and `images/fulls/` — portfolio gallery images paired by filename (e.g., `01.jpg` in both dirs).

## Big picture / why
Static GitHub Pages site (repo: `daniloldn.github.io`) — changes to `main` branch auto-deploy. Uses HTML5 UP template for professional portfolio with responsive design. The site combines both source (Sass) and compiled assets for development simplicity. No build pipeline required — just compile Sass manually when making style changes.

## Editing rules (concrete)
- For styling changes: edit `assets/sass/*.scss` and the partials in `assets/sass/libs/`. Then compile to `assets/css/main.css`.
- For behavior: update `assets/js/main.js`. Do not change vendor `*.min.js` files unless you intend to upgrade the library.
- For gallery images: add matching files to `images/thumbs/` and `images/fulls/` with the same filename (e.g., `01.jpg`), because `index.html` links thumbs to fulls.

## Common commands (local testing & build)
Test locally and compile Sass from project root:

```bash
# Quick local server (Python)
python -m http.server 8000

# Sass compile (single file):
sass assets/sass/main.scss assets/css/main.css --no-source-map --style=compressed

# Watch Sass and auto-rebuild (use while editing):
sass --watch assets/sass:assets/css
```

Note: No package.json or build tools — vanilla Sass compilation only. Add npm/tooling if needed and update these instructions.

## Patterns and examples to follow
- SASS partials: `_vars.scss` contains theme variables — change colors/sizes here.
- Breakpoints and grid are handled by `libs/_breakpoints.scss` and `_html-grid.scss` — use existing mixins rather than adding ad-hoc media queries.
- JS initializes parallax effects in `assets/js/main.js` — parallax disabled on mobile/IE for performance.
- Gallery: Portfolio items in `index.html` section `#two` link thumbnails to full images via filename matching.

## Integration points & caveats
- GitHub Pages: pushing to `main` will update the live site. Be careful with large image additions — keep thumbnails small to avoid slow page loads.
- Fonts: `webfonts/` and a remote Google font are used; verify licensing when changing fonts.

## PR / commit guidance
- Small, focused PRs are easiest: e.g., "Update hero copy" or "Regenerate CSS after Sass changes".
- When regenerating `assets/css/main.css`, include the source `.scss` change in the same PR so reviewers can see intent.

## Troubleshooting quick hits
- CSS changes not visible: ensure you edited `assets/sass` and recompiled to `assets/css/main.css` and hard-refresh the browser (clear cache).
- Gallery thumbs not showing: confirm filename exists in both `images/thumbs/` and `images/fulls/` and markup in `index.html` uses that filename.

If any part of this guidance is unclear or you want different conventions (introduce npm, automated image resizing, CI deploy, etc.), tell me and I will update this file.
