# CLAUDE.md

Guidance for Claude Code when working in this repository.

## What this is

A collection of standalone, single-file browser tools hosted via **GitHub Pages
(Jekyll)**. Each tool is one self-contained `.html` file at the repo root. There
is no build step, package manager, or backend — everything runs client-side in
the browser.

## Conventions

- **One file per tool.** Each page bundles its own HTML, CSS (in a `<style>`
  block), and JavaScript (in a `<script>` block). No local companion CSS/JS
  files and no bundler — but see the CDN note below.
- **CDN libraries are allowed.** You can pull in JS/CSS libraries from a CDN
  (e.g. a charting or date library via `<script src="https://...">`) when it
  genuinely helps. Keep the page working as a single file — no local build
  artifacts. Prefer well-known, reliable CDNs and pin a version.
- **No React.** Stick to vanilla JS (optionally aided by small CDN
  libraries). No React, no JSX, no build tooling.
- **Shared visual language.** Tools follow a common card-based design. Reuse the
  CSS custom properties and layout from an existing tool (e.g. `riegel.html`):
  - `:root` variables: `--primary: #2563eb`, `--bg: #f8fafc`, `--card: #ffffff`,
    `--text: #1e293b`, `--border: #e2e8f0`, `--secondary: #64748b`
  - Centred `.container` (max-width ~450px) card with rounded corners and a soft
    shadow, system font stack, `.toggle-container` pill toggles, and a `.results`
    box for output.
- **Persist inputs where it helps.** Some tools save state to `localStorage`
  (see `riegel.html`); do this when it improves the experience.
- **`index.html`** auto-lists every `.html` file except itself via Jekyll/Liquid.
  New tools appear automatically — no need to edit it.
- Keep third-party services free and keyless where possible (e.g. the crow-flies
  tool uses OpenStreetMap's Nominatim). Respect each service's usage policy.

## Adding a new tool

1. Create `some-tool-name.html` at the repo root (kebab-case filename).
2. Copy the structure/styles from an existing tool for consistency.
3. That's it — `index.html` picks it up automatically.

## Git

- `main` is the default branch. Develop on a feature branch and push there;
  don't open a PR unless asked.
