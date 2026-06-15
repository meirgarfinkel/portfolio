# Portfolio — Project Spec

> Personal portfolio / landing page for Meir Garfinkel.
> Single static page, no build step. Source of truth for scope and structure.

---

## 1. Overview

A single-page personal portfolio served as static files. It presents identity, a short
about, skills, recent work, and featured projects, with links out to LinkedIn, GitHub,
and email. The aesthetic is a dark "glassmorphism" theme over a cursor-reactive
background grid.

- **Live:** https://meirgarfinkel.com
- **Goal:** lightweight, fast-loading, dependency-free shop window for engineering work.

## 2. Stack & Constraints

- **Plain HTML + CSS + a few lines of vanilla JS.** No framework, no bundler, no
  package manager, no build step.
- All assets are local and root-relative (`/styles.css`, `/icons/*.svg`, favicons).
- Single page: `index.html`. All styling in `styles.css`.
- PWA-ready via `site.webmanifest` + favicons/android-chrome icons.

## 3. Structure

```text
index.html          # the entire page (markup + inline year/grid script)
styles.css          # all styling (CSS variables, glass, grid, layout)
site.webmanifest    # PWA manifest
icons/              # inline-referenced UI svgs (linkedin, github, email, online)
favicon*.{ico,png}  # favicons
android-chrome-*.png
LICENSE
```

### Page sections (in `index.html`)

1. **Header** — name, tagline, "Open to software opportunities" pill.
2. **About** — intro title + body.
3. **Two-col** — Contact & Links card (LinkedIn/GitHub/Email) + Skills & Stack pills.
4. **Recent Work** — bulleted experience list.
5. **Featured Projects** — project cards (RAG platform, Shefa) with tags + live-demo CTA.
6. **Footer** — auto-updated copyright year.

## 4. Styling System

- CSS custom properties in `:root` drive colors, radius, max-width, spacing
  (`--bg`, `--accent`, `--text`, `--muted`, `--border`, `--radius`, `--max-width`).
- `.glass` is the reusable frosted-card treatment (used by `.pill`, `.project-card`).
- `.bg-grid` is a fixed full-viewport grid; a `::after` layer reveals an accent-colored
  grid in a radial mask that follows the cursor (`--mx`/`--my` set by JS on `mousemove`).
- Responsive: `.two-col` collapses to one column and the header stacks at `max-width: 800px`.

## 5. JavaScript

Inline in `index.html`, two responsibilities only:

1. Set footer year from `new Date().getFullYear()`.
2. Track cursor and update `--mx`/`--my` on `.bg-grid` for the reactive glow.

## 6. Deployment

Static hosting on the `meirgarfinkel.com` apex. Subdomains host the live project demos
(`rag-ml.meirgarfinkel.com`, `shefa.meirgarfinkel.com`). No CI/build — pushing the
static files is the deploy.

## 7. Featured Projects

| Project | Demo | Summary |
|---------|------|---------|
| RAG Platform | https://rag-ml.meirgarfinkel.com | End-to-end retrieval-augmented generation: ingestion → vector index → grounded answers over a FastAPI backend. |
| Shefa | https://shefa.meirgarfinkel.com | Free, nonprofit job board for people without experience — no résumés, no credential gatekeeping, message-based applications. |
