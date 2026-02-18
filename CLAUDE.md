# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static splash/landing page for **Balise IA** — an AI-powered regulatory navigation tool for citizens and municipal teams in Quebec. The site is bilingual (French/English) with no build step, framework, or dependencies.

- The main Balise IA app is located at /Users/colin/dev/src/balise/ingest see /Users/colin/dev/src/balise/ingest/CONTEXT.md
- This landing page is live at http://balise.ai and is handled by cloudflare directly from the Github https://github.com/colinsurprenant/balise-splash project.

## Architecture

- `index.html` — French landing page (primary, `lang="fr"`)
- `index_en.html` — English landing page (`lang="en"`)
- `assets/` — Logo and static assets
- Pages link to each other via the language switcher in the header
- All CSS is inlined in `<style>` tags within each HTML file (no external stylesheet)
- The app itself lives at `https://app.balise.ai/` (separate repo)

## Development

Open `index.html` directly in a browser. No build, no server required.

## Design Tokens

- Brand color: `#9C1B20` (dark red), hover: `#7a1519`
- Background: `#fafafa`, card: `white`, border-top accent: 4px solid brand color
- Font stack: `-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif`
- Background uses a subtle sonar/isobath radial-gradient pattern (bottom-left origin)

## Key Conventions

- Content changes must be applied to **both** `index.html` and `index_en.html` to keep translations in sync
- Styles are duplicated across both files — CSS changes must be mirrored in both