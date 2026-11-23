# AGENTS.md — Portfolio Website Project

Project Assistant role: support the Lead Engineer on the personal portfolio site.

## Project Overview

A customized, **bilingual (de/en)** Start Bootstrap "Freelancer" Bootstrap 5 one-page portfolio
theme, personalized for **Dipl.-Ing. Jürgen Kratochwill** (Lead Engineer, Munich). It showcases
industrial/embedded software projects (C++, Qt, OpenCV, FPGA, MQTT, embedded Linux) via a responsive
grid and modal detail windows.

- **Owner / Lead Engineer:** Dipl.-Ing. Jürgen Kratochwill
- **Live site:** `portfolio.kwilleng.de` (see `docs/CNAME`)
- **Remote:** `https://github.com/rejuce/portfolio`
- **Default branch:** `master` · **Working branch for this work:** `dev`
- **Theme origin:** Start Bootstrap "Freelancer" (v7.0.7, MIT)

## How this repo works (IMPORTANT)

This is a **static, hand-authored site**. The source of truth is the `docs/` directory — the finished,
published HTML/CSS/JS. There is **no build step** and no source→build pipeline. Edits are made directly
in `docs/`; keep `index-en.html` and `index-de.html` in sync when content changes.

The original `src/` (Pug/SCSS/JS) and `scripts/` (build/render/watch) were **removed** — they only
produced a single-language build and are not part of this bilingual site. Do not try to rebuild.

## Repository Layout

```
portfolio/
├── docs/                    # SOURCE OF TRUTH — built / published, tracked in git
│   ├── index.html           # lang-redirect → index-en.html / index-de.html
│   ├── index-en.html        # English site (hand-edited; 11 portfolio items + modals 1–11)
│   ├── index-de.html        # German site (hand-edited)
│   ├── impressum.html       # Legal notice
│   ├── css/styles.css       # Compiled CSS
│   ├── js/scripts.js        # Theme JS
│   ├── assets/              # Images, favicon, logo (img/portfolio/*, kwillEngLogoSmallAlpha.png)
│   └── CNAME                # portfolio.kwilleng.de
├── README.md                # Project overview + how to make edits
├── package.json             # Minimal metadata only (no build scripts)
├── .gitignore               # node_modules, .DS_Store
├── .editorconfig            # 4-space indent, final newline, trim trailing whitespace
└── LICENSE                  # MIT
```

## Key Conventions & Notes

- **No build toolchain.** `docs/` is the source of truth; there is nothing to compile or bundle.
- **Multilingual:** `index.html` redirects to `index-en.html` / `index-de.html` based on
  `navigator.language`. Always mirror content changes across both language files.
- **Portfolio items:** 11 projects, each with a modal (`portfolioModal1` … `portfolioModal11`),
  duplicated in both language files.
- **Contact form:** Formspree endpoint (`https://formspree.io/f/xyzjazrj`) — no backend in repo.
- **Editorconfig:** 4-space indentation, final newline, no trailing whitespace (except `.md`).

## Portfolio Items (Modals)

1. Distributed Industrial Measurement System — 48 embedded Linux devices, edge SBC, Ethernet/SPI/I2C/FPGA
2. Next-Gen Sensor Platform — CAN/USB/Ethernet/I2C, REST API
3. High Speed Edge Characterization — C++/OpenMP/OpenCV, 1GB/s, MQTT
4. Qt Commission/Service App — sockets, MQTT, REST
5. Qt Industrial Control and Inspection — camera arrays, barcode recall, CPU-GPU processing
6. Qt Operator Guide — Beckhoff PLCs via MQTT
7. 2D-3D Data Fusion — inspection cameras + 3D profile sensors, MQTT/I/O
8. Windows Like Linux Task Manager — open source, github.com/rejuce/LikeTaskManager
9. Texture Analysis — OpenCV, OpenMP, GPU co-processing
10. Industrial Image Processing — sample-validated core algorithm for a client's industrial-inspection problem (uncertainty, varying lighting, transparency); asset `cupprocessor.{svg,png}`
11. LocalAI Deployments — full on-premise LocalAI stack (RAG over 100k+ docs + live JIRA ingestion, fully local interface, local dev agent); asset `localai.{svg,png}`

## Working Rules

- **Never commit or push without explicit approval.**
- Make focused, minimal changes; do not touch unrelated files.
- When editing content, update BOTH `index-en.html` and `index-de.html` (keep them in sync).
- Do not expose secrets, credentials, tokens, or private config.
- Keep `agent/progress.md` and `agent/outline.md` updated as work progresses.
