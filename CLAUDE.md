# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

`balise-splash` is the marketing/splash page for **Balise** — AI-enabled regulatory navigation for Quebec municipalities, MRCs, and citizens. The splash exists in two languages (FR default at `index.html`, EN at `index_en.html`) and is deployed as a static page.

Both files contain the same content and styles; the only difference is the language. Keep them in sync when making changes.

- The main Balise app is located at `/Users/colin/dev/src/balise/ingest` — see `/Users/colin/dev/src/balise/ingest/CONTEXT.md`.
- This landing page is live at https://balise.ai and is served by Cloudflare directly from the GitHub repo https://github.com/colinsurprenant/balise-splash.
- The product app itself lives at https://app.balise.ai/ (separate repo).

## Visual identity

The brand uses a **Trail Blaze** identity — two stacked rectangles (red on top, navy below) referencing the painted hiking-trail markers. Logo file: `assets/balise-mark.svg`. Always use SVG.

### Tokens
- `--navy: #0F2742` — structure: type, plates, dividers, icons
- `--red: #C8362F` — action only: CTAs, links, signal accents (use sparingly)
- `--paper: #ffffff` — primary surface
- `--paper-2: #f6f4ee` — secondary grouped surfaces
- Fonts: **Manrope** (UI/body/headings), **DM Mono** (labels/eyebrows/metadata)

### Color contract
Navy carries structure. Red is the signal color — reserved for CTAs, links, the blaze tab on cards, the audience-stat footer. Don't drift; the meaning of red depends on its scarcity.

### Headline pattern
Action verb that activates the navigation metaphor + regulatory domain. FR: "Naviguez la réglementation municipale." EN: "Navigate municipal regulations." H1 is `white-space: nowrap` and sized with `clamp(1.4rem, 5.2vw, 2.4rem)` so it always fits on one line.

### Bilingual
The mark never changes between FR and EN. The wordmark switches "AI" (en) ↔ "IA" (fr). Use the `<span class="ai">…</span>` suffix pattern so styling stays consistent.

## File structure

```
balise-splash/
├── index.html          # FR (default)
├── index_en.html       # EN
├── assets/
│   └── balise-mark.svg # Logo
├── CLAUDE.md           # this file
├── BRAND_HANDOFF.md    # full brand reference (for propagating to the app)
└── README.md
```

## Working rules

- When updating copy, modify BOTH `index.html` and `index_en.html` in the same change.
- Never recolor the mark blocks (they encode trail-blaze semantics).
- Never offset the top block (changes the symbol's meaning to "turn").
- Keep the CSS in `<style>` blocks at the top of each file (no external stylesheets — the splash must be a fully self-contained static page).
- Reuse the existing component patterns (cards with red blaze tab, jurisdiction band with three pillars, status grid, etc.) — don't invent new structures.
- See `BRAND_HANDOFF.md` for the full brand reference if propagating styles to the broader product.

## Development

Open `index.html` directly in a browser. No build, no server required.

## Deployment

Static HTML, no build step. Cloudflare serves `index.html`, `index_en.html`, and `assets/` directly from the GitHub repo.
