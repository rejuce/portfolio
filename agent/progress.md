# Progress Log

Working branch: `dev` (created from `master`). Never commit/push without explicit approval.

## 2026-11-17 — Initial setup & repository mapping

- [x] Cloned `https://github.com/rejuce/portfolio` into `/workspace/repos/portfolio` (5252 objects).
- [x] Created and switched to the `dev` branch (working tree clean).
- [x] Created the `agent/` subfolder.
- [x] Mapped the repository: inspected `src/`, `docs/`, `scripts/`, `package.json`, `README.md`,
      `.gitignore`, `.editorconfig`, and `docs/CNAME`.
- [x] Read `docs/index-en.html` to understand the personalization, multilingual setup, and the 9
      portfolio items / modals.
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
- 9 portfolio items; modals 1–9 are hand-edited in both `index-en.html` and `index-de.html`.
- Contact form uses a Formspree endpoint; no backend in repo.

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
