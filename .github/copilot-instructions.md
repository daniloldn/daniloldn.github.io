## Quick orientation

This repository is a static personal site (HTML/CSS/JS) built from the "Strata" HTML5 UP template.
Key directories:
- `index.html`, `dissertation.html` — site entry pages.
- `assets/sass/` — Sass source (edit here). Notable files: `main.scss`, `libs/_vars.scss`, `libs/_mixins.scss`.
- `assets/css/main.css` — compiled CSS (do not edit directly; regenerate from Sass).
- `assets/js/` — JS behavior; vendor libs are stored as `*.min.js`. Edit `assets/js/main.js` for custom behavior.
- `images/fulls/` and `images/thumbs/` — gallery images are paired by filename (thumbs used on index, full images opened by the gallery).

## Big picture / why
The site is a static GitHub Pages site (repository name `daniloldn.github.io`); changes pushed to `main` will publish the site. The author maintained both source (Sass) and compiled assets for simplicity — prefer editing source where present.

## Editing rules (concrete)
- For styling changes: edit `assets/sass/*.scss` and the partials in `assets/sass/libs/`. Then compile to `assets/css/main.css`.
- For behavior: update `assets/js/main.js`. Do not change vendor `*.min.js` files unless you intend to upgrade the library.
- For gallery images: add matching files to `images/thumbs/` and `images/fulls/` with the same filename (e.g., `01.jpg`), because `index.html` links thumbs to fulls.

## Common commands (local testing & build)
Open and test the site locally with a static server (recommended) from the repo root:

```powershell
# Quick local server (Python)
python -m http.server 8000

# Sass compile (single file):
sass assets/sass/main.scss assets/css/main.css --no-source-map --style=compressed

# Watch Sass and auto-rebuild (use while editing):
sass --watch assets/sass:assets/css
```

Notes: there is no package.json or bundler detected. If you add tooling (npm, gulp, etc.), commit the manifest and update these instructions.

## Patterns and examples to follow
- SASS partials: `_vars.scss` contains theme variables — change colors/sizes here.
- Breakpoints and grid are handled by `libs/_breakpoints.scss` and `_html-grid.scss` — use existing mixins rather than adding ad-hoc media queries.
- JS initializes Poptrox gallery and parallax in `assets/js/main.js` — change captions or selector there (see the section with id "two"; selector: `.work-item a.image`).

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
