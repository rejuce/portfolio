# Repository Outline — portfolio (rejuce/portfolio)

Customized, bilingual (de/en) Start Bootstrap "Freelancer" Bootstrap 5 portfolio theme for
Dipl.-Ing. Jürgen Kratochwill (Munich). Live at `portfolio.kwilleng.de`.

## Build status
- **No build toolchain.** The site is static and hand-authored; `docs/` is the source of truth.
- The original `src/` (Pug/SCSS/JS) and `scripts/` (build/render/watch) were removed — they only
  produced a single-language build and are not part of this bilingual site.

## Root
- `README.md` — Project overview, how the repo works, and how to make edits.
- `package.json` — Minimal metadata only; no build scripts.
- `.gitignore` — ignores `node_modules`, `.DS_Store`
- `.editorconfig` — 4-space indent, final newline, trim trailing whitespace (`.md` off)
- `LICENSE` — MIT

## docs/ (built / published — tracked in git — SOURCE OF TRUTH)
- `index.html` — language redirect → `index-en.html` / `index-de.html` (per `navigator.language`)
- `index-en.html` — English site (hand-edited; 9 portfolio items + modals 1–9)
- `index-de.html` — German site (hand-edited)
- `impressum.html` — legal notice
- `css/styles.css` — compiled CSS
- `js/scripts.js` — theme JS
- `assets/` — built assets:
  - `favicon.ico`, `faviconOld.ico`
  - `img/avat.jpg`, `img/avataaars.svg`
  - `img/portfolio/` — project images (ids, hcx, abis, wm, spri, tex, sqlv, ltm, uml, etc.)
  - `kwillEngLogoSmallAlpha.png` — owner's logo
- `CNAME` — `portfolio.kwilleng.de`

## Portfolio items (9)
1. Distributed Industrial Measurement System (`portfolioModal1`)
2. Next-Gen Sensor Platform (`portfolioModal2`)
3. High Speed Edge Characterization (`portfolioModal3`)
4. Qt Commission/Service App (`portfolioModal4`)
5. Qt Industrial Control and Inspection (`portfolioModal5`)
6. Qt Operator Guide (`portfolioModal6`)
7. 2D-3D Data Fusion (`portfolioModal7`)
8. Windows Like Linux Task Manager — open source, github.com/rejuce/LikeTaskManager (`portfolioModal8`)
9. Texture Analysis (`portfolioModal9`)

## Notes
- Each portfolio item is a modal in both language files; keep `index-en.html` and `index-de.html`
  in sync when editing content.
- Contact form posts to Formspree (`https://formspree.io/f/xyzjazrj`); no backend in repo.
