# Portfolio — Handoff

Quick orientation for anyone (human or agent) picking this up.

## What it is

A single static HTML page (`index.html`) styled by `styles.css`, deployed to
https://meirgarfinkel.com. No framework, no build, no dependencies. Edit the files,
push, done. See `project_spec.md` for the full structure.

## How to run it locally

It's static — open `index.html` directly, or serve the folder:

```bash
python3 -m http.server 8000   # then visit http://localhost:8000
```

Use a server (not `file://`) so the root-relative paths (`/styles.css`, `/icons/*`)
resolve.

## How to make common changes

- **Add a project:** copy an `<article class="project-card glass">` block inside
  `<section class="featured">` and edit the title, body, `.project-tags`, and CTA href.
- **Edit skills:** add/remove `<div class="pill glass">…</div>` items in the Skills column.
- **Change colors/spacing:** edit the CSS variables in `:root` in `styles.css`.
- **Update links/contact:** the `.links-grid` in the Contact card.

## Conventions

- Asset paths are root-relative (`/styles.css`, `/icons/foo.svg`). Keep them that way.
- External links use `target="_blank"` + `rel="noopener noreferrer"`.
- Keep it dependency-free and build-free — that is the point of this project.

## Known follow-ups / nice-to-haves

- No Open Graph / Twitter card meta tags (social-share previews are bare).
- `site.webmanifest` `theme_color` (`#0f172a`) differs from the page `--bg` (`#020617`).
- A few CSS classes were unused and have been removed (`.links`, `.skills-section`,
  `.text-green`, `.highlight`) — re-check `styles.css` before assuming a class exists.
