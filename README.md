# Portfolio — Dipl.-Ing. Jürgen Kratochwill

A bilingual (German / English) personal portfolio site built on the
[Start Bootstrap "Freelancer"](https://startbootstrap.com/theme/freelancer/)
Bootstrap 5 theme.

**Live site:** <https://portfolio.kwilleng.de>

## How this repo works

This site is a **static, hand-authored** site. The source of truth is the
`docs/` directory — the finished, published HTML/CSS/JS. There is **no build
step** and no source→build pipeline.

```
docs/
├── index.html          # Language redirect → index-en.html / index-de.html
├── index-en.html       # English site (hand-edited)
├── index-de.html       # German site (hand-edited)
├── impressum.html      # Legal notice
├── css/styles.css      # Compiled CSS
├── js/scripts.js       # Core theme JS
├── assets/             # Images, favicon, logo
└── CNAME               # portfolio.kwilleng.de
```

## Making edits

1. Edit the relevant file(s) under `docs/`.
2. Keep `index-en.html` and `index-de.html` in sync when content changes.
3. Commit and push. The site is served directly from these files.

Each portfolio item is a modal (`portfolioModal1` … `portfolioModal9`) in both
language files.

## Notes

- The original Start Bootstrap theme source (`src/`) and build toolchain
  (`scripts/`) were removed — they only produced a single-language build and
  are not part of this bilingual site. The upstream theme is MIT licensed
  (see `LICENSE`).
- `package.json` is kept only as minimal metadata; there are no build scripts.
