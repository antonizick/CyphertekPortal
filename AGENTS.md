# AGENTS.md — CyphertekPortal

## Project overview

Single-file static HTML site deployed from `index.html`. No build tools, no package manager, no frameworks.

## Key files

| File | Purpose |
| --- | --- |
| `index.html` | All HTML, CSS, and JS in one file (~1100 lines) |
| `data/nav.json` | Navigation structure — all nav links live here |

## Navigation architecture

The desktop dropdown nav and mobile accordion nav are both **rendered client-side** from `data/nav.json` via `fetch()`. To add/remove/reorder links, **edit `data/nav.json` only**. Do not hardcode nav items in HTML.

The JSON shape:
```json
{ "sections": [ { "label": "...", "href": "..." /* optional parent link */, "links": [ { "label": "...", "href": "..." } ] } ] }
```

Sections with a single link (like "Shopping") still get a dropdown arrow. The section-level `href` is used for desktop nav's parent `<a>`.

## Color scheme / design

All colors use CSS custom properties in `:root` at the top of `index.html`. Key variables: `--dark`, `--mid`, `--primary`, `--accent`, `--accent-glow`, `--text`, `--text-dim`, `--card-border`, `--glass`, `--nav-bg`. Update these for theme changes.

## Constraints

- **No build step** — any change is live after saving `index.html` or `data/nav.json`.
- **`fetch()` requires HTTP** — opening `index.html` via `file://` will fail to load `data/nav.json`. A local server is needed.
- **Single file** — all CSS and JS are inlined in `<style>` and `<script>` blocks.
- Remote images loaded from `https://www.antonizick.com/cyphertek/i/` and `https://www.antonizick.com/cyphertek/img/`.

## Git

Remote: `https://github.com/antonizick/CyphertekPortal.git`
Branch: `main`
