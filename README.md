# Hazy Space Ranger Studios

Landing page for **Hazy Space Ranger Studios**, a Chicago-based tabletop board game studio.

A self-contained single-page site built with vanilla HTML/CSS/JS and a Three.js
WebGL particle starfield. Features a halftone-forming racing-stripe motif, an
animated badge logo, a typewriter intro, and an interactive cosmic background.

## Live site

Published with GitHub Pages from the [`src/`](src/) folder.

## Local development

The site is a single static file with no build step. Serve the `src/` folder
with any static server, for example:

```bash
npx serve src -l 3000
```

Then open http://localhost:3000.

## Structure

```
src/
├── index.html        # The entire site (inline CSS + JS)
└── assets/           # Logo art, icons, and supporting assets
```
