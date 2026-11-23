# Progress Log

Working branch: `dev` (created from `master`). Never commit/push without explicit approval.

## 2026-11-17 — Initial setup & repository mapping

- [x] Cloned `https://github.com/rejuce/portfolio` into `/workspace/repos/portfolio` (5252 objects).
- [x] Created and switched to the `dev` branch (working tree clean).
- [x] Created the `agent/` subfolder.
- [x] Mapped the repository: inspected `src/`, `docs/`, `scripts/`, `package.json`, `README.md`,
      `.gitignore`, `.editorconfig`, and `docs/CNAME`.
- [x] Read `docs/index-en.html` to understand the personalization, multilingual setup, and the 9
      portfolio items / modals (11 as of 2026-11-23).
- [x] Wrote `agent/AGENT.md` (project overview, layout, conventions, portfolio items, working rules).
- [x] Wrote `agent/outline.md` (structured file-by-file repository map).
- [x] Wrote this `agent/progress.md` log.

## 2026-11-17 — Strip the dormant build pipeline

- [x] Confirmed the build toolchain is dormant: all scripts in `scripts/` output to an unused
      `dist/` directory (verified by reading every build/render/watch script). The build produces a
      single-language site and never touches the bilingual `docs/` output.
- [x] Deleted `src/` (Pug/SCSS/JS source — only covered modals 1–6, already out of sync with the
      real bilingual site).
- [x] Deleted `scripts/` (12 build/render/watch scripts).
- [x] Rewrote `package.json` as minimal metadata (removed build/start/clean scripts and all
      devDependencies).
- [x] Replaced `README.md` with a short note explaining `docs/` is the source of truth and how to
      make edits.
- [x] Updated `agent/AGENT.md`, `agent/outline.md`, and this log to reflect the new state.

### Key findings (corrected)
- Customized Start Bootstrap "Freelancer" theme (v7.0.7) for Dipl.-Ing. Jürgen Kratochwill, Munich.
- Live at `portfolio.kwilleng.de` (`docs/CNAME`).
- `docs/` is the source of truth (hand-authored, bilingual); there is **no build step**.
- The original `src/` + `scripts/` build toolchain was vestigial (single-language, outputs to unused
  `dist/`) and has now been removed.
- 11 portfolio items; modals 1–11 are hand-edited in both `index-en.html` and `index-de.html`.
- Contact form uses a Formspree endpoint; no backend in repo.

## 2026-11-23 — Add two new portfolio showcases (Industrial Image Processing + LocalAI)

- [x] Added **Industrial Image Processing** (`portfolioModal10`, caption `Industrielle Bildverarbeitung`)
      describing a client's complex industrial-inspection problem (uncertainty, varying lighting,
      transparency) solved with a sample-validated core algorithm integrated into the client's own
      software.
- [x] Added **LocalAI Deployments** (`portfolioModal11`, caption `LocalAI-Deployments`) describing a
      full on-premise LocalAI stack for a small engineering firm (RAG over 100k+ docs + live JIRA
      ingestion, fully local interface for sensitive topics, local dev agent).
- [x] Added `LocalAI` to the core-competencies masthead in both `index-en.html` and `index-de.html`.
- [x] Created new assets `docs/assets/img/portfolio/cupprocessor.png` and
      `docs/assets/img/portfolio/localai.{svg,png}` (PNG via headless Chromium).
- [x] Added 2 grid items + 2 modals to both language files, keeping them in sync.
- [x] Fixed a **pre-existing charset bug** in `index-de.html`: `<meta charset="utf-t" />` →
      `utf-8`. This bug was corrupting all German umlauts and directly affected my new umlaut
      content, so the fix was warranted. Confirmed pre-existing on `master`.
- [x] Verified: 11 grid items, 11 modals, 4 new-asset refs each, 22 modal refs each in both files.
- [x] Served on port 8080 (all assets return 200) and rendered headless Chromium screenshots of
      both EN and DE pages — layout verified, new items appear correctly, DE umlauts now render
      correctly.
- [x] **Asset fixes (2026-11-23):**
      - Industrial Image Processing: used the actual attached screenshot (`arbitarytilts.png`,
        UUID `7fcc1104`) that was saved to disk. The screenshot is very wide (1983×610, ratio 3.25:1,
        10 debug cells) but the dominant card format is 640×385 (ratio 1.66:1). After testing crop
        options, decided to **crop to 640×385 showing the left portion** (matching the exact card
        size) — the 3 red-X failures + green circles are shown; the right half of the grid is cut
        off. Resized from the 1014×610 crop to 640×385 via LANCZOS. Verified in full EN and DE page
        renders and in a modal (`col-lg-8`) render — displays correctly at card size.
      - LocalAI: aligned all four bubble labels to the "Secure topics" convention (25px inside the
        box left edge, baseline 10px above the box bottom). Previously "100k+ documents" and
        "Live JIRA ingestion" sat on the bottom border and "Local dev agent" was misaligned.
      - Server on :8080 returns 200 for both updated assets (cupprocessor.png 1099478B, localai.png 178415B).

## 2026-11-23 — Add the company logo to the homepage (navbar + footer)

- [x] Added the owner's company logo (Kratochwill Engineering) in two best-fit locations on both
      `index-en.html` and `index-de.html`:
      - **Navbar:** replaced the placeholder "Start" brand text with the transparent-background
         icon (`kwillEngLogoSmallAlpha.png`, 345×388) as the navbar-brand. Chosen over the solid-white
         full logos (`kwillEngLogoFull.png` 1408×768, `kwillEngLogoSmall.png` 345×388) because the
         dark navbar (`#2c3e50`) would show a white box.
      - **Footer:** centered the larger transparent-background icon
         (`kwillEngLogoSmallerAlpha.png`, 914×564) above the three footer columns with a subtle
         drop-shadow so it blends on the dark footer.
- [x] Added CSS to `docs/css/styles.css` (`.navbar-brand-logo`, `.footer-logo`, `.footer-logo-img`):
         logo sized for the navbar with a shrink-transition to match `navbar-shrink`, and footer logo
         centered with a drop-shadow.
- [x] Kept `index-en.html` and `index-de.html` in sync (both navbar and footer edits mirrored).
- [x] Verified: served on port 8080 — `index-en`, `index-de`, and both logo assets return HTTP 200.
- [x] Rendered headless Chromium screenshots of EN (top + footer) and DE (top) pages. The green
         hexagon icon displays correctly in the navbar and the full logo in the footer on both
         languages, with no white box and good contrast on the dark backgrounds.

### Logo variant selection
| File | Size | Background | Used |
|---|---|---|---|
| `kwillEngLogoFull.png` | 1408×768 | solid white | ❌ (white box on dark bars) |
| `kwillEngLogoSmall.png` | 345×388 | solid white | ❌ (white box on dark bars) |
| `kwillEngLogoSmallAlpha.png` | 345×388 | transparent (icon) | ✅ navbar |
| `kwillEngLogoSmallerAlpha.png` | 914×564 | transparent (icon) | ✅ footer |
| `logo.ico` | 32×32 | — | favicon (left alone) |

### Logo size tuning (2026-11-23)
- The footer logo initially rendered too small. The engineer requested ~2× the default size.
- Investigated whether Bootstrap's `.img-fluid { height: auto }` (styles.css:601) was overriding
  `.footer-logo-img { height }` (the footer `<img>` carries both classes). Confirmed it is **not**
  overriding: `.footer-logo-img` (line 11063) comes *after* `.img-fluid` (line 601) with equal
  specificity, so it wins the cascade and the `height` takes effect. Verified by rendering the
  standalone footer test page (real served CSS + logo) at 2.25rem / 3rem / 6rem — the logo scaled
  correctly each time (2.25/3rem were too small and visually similar; 6rem is correct).
- Set `.footer-logo-img { height: 6rem }` (styles.css:11063) — ~2× the too-small default, matching
  the engineer's request. No `!important` needed.
- **Navbar logo size correction (2026-11-23):** The engineer reported the header symbol was also
  "totally off" / too big. The navbar logo (`.navbar-brand-logo`) had been set to `height: 1.75rem`
  (shrink → `1.25rem`). I first reduced it to `1rem` then `0.85rem` and rendered full-page (headless
  Chromium, real served CSS) — but the engineer reported the navbar logo was *also* too small. Set
  back to `height: 1.75rem` (shrink → `1.25rem`), which renders proportionally in the 60px navbar.
- **Footer logo size (2026-11-23):** The engineer said the footer logo was still too small at 6rem.
  Bumped to 8rem, then settled at **7rem** after visual verification in the actual browser (see
  below). No `!important` needed.
- **Verified in the real browser (2026-11-23):** The engineer opened a browser in the virtual desktop
  (Xvfb display :40, 1280×800 kiosk chromium, pid 9186). I focused it with `xdotool`, navigated to
  `http://localhost:8080/index-de.html`, and screenshot with `scrot` (`/tmp/user_site_v3.png`).
  Served CSS confirmed via curl at each step. Result: navbar logo at 1.75rem proportional; footer
  logo at 7rem shows the full logo (icon + "KRATOCHWILL-ENGINEERING" wordmark) centered above the
  three columns, no white box, good contrast on the dark footer (`#2c3e50`).
- **Logo color fix (2026-11-23):** The engineer reported the green logo blends into the dark blue
  background (`#2c3e50`) — not a size problem, a color-compatibility problem. Created white versions:
  `kwillEngLogoSmallWhite.png` (navbar) and `kwillEngLogoSmallerWhite.png` (footer) via `convert`
  (`-alpha extract -threshold 12% -fill white -alpha set`). Applied to both `index-en.html` and
  `index-de.html`. The engineer later replaced these with cleaner hand-made white assets (same
  filenames), so HTML references remain valid.
- **Navbar size + shrink-state fix (2026-11-23):** The engineer reported the navbar logo was too large
  in the expanded state and too small in the shrink state (scroll). Previously `7rem` expanded /
  `1.25rem` shrink — a jarring 5.6× jump. Set expanded to `3.5rem` and shrink to `2.5rem` (a smooth
  1.4× transition). Navbar padding kept at 10px so expanded height ≈ original 76px. Footer bumped
  20%: `10rem` → `12rem`. Verified both states in the real browser (expanded `/tmp/user_site_v8.png`,
  shrink `/tmp/user_site_v9.png`).
- **Committed + pushed (2026-11-23):** Commit `757e5e3` on `dev` — "Add company logo to homepage navbar and footer" — 7 files changed, 115 insertions. Pushed via deploy key
  (`GIT_SSH_COMMAND="ssh -i ~/.ssh/id_portfolio_deploy" git push origin dev`) → `80ba7f0..757e5e3 dev -> dev`.
- **⚠️ Limitations:** Headless Chromium full-page renders at 1920×1080 were used as an interim
  check but **do not** match the engineer's actual browser (resolution, zoom, OS). The final
  confirmation is the scrot screenshot of the real browser at 1280×800. The engineer should still
  confirm sizes in their own browser — the 1280×800 desktop may differ from their typical setup.

## Next steps (pending approval / further instruction)
- Update `docs/index-de.html` in parallel with `docs/index-en.html` when editing English content.
- Approve commit + push (requires the correct SSH key — see repo notes) when ready.

## 2026-11-17 — Create a GitHub deployment keypair for the portfolio repo

- [x] Generated a new ed25519 keypair for use as a GitHub deployment key on `rejuce/portfolio`.
- [x] Stored it **outside** the git repo at `/workspace/repos/keys/portfolio/` (private key `portfolio`,
      public key `portfolio.pub`), following the existing convention under `/workspace/repos/keys/`.
- [x] Permissions: `portfolio` = `600`, `portfolio.pub` = `644`.
- [x] Public key comment: `portfolio-deploy-key@kwilleng`.
- [x] Fingerprint: `SHA256:vdgraqnOP3nWYawMuNQvU30683qr17sY1pNY0QvCn1k` (ed25519).

### Public key (add this to the repo's Settings -> Deploy keys on GitHub)
```
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIAMvs3OOWluEHMAbdb9/UM8cF6PIfo3xNPZ/36DYlFSP portfolio-deploy-key@kwilleng
```