# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a single-file static HTML demo page — `Home.html` — for "ING SymphonyAI" (subtitled "The Editorial Intelligence Dashboard"). It is a prototype/demo, not a production app with a build pipeline.

## Architecture

- **Single file:** All HTML, CSS (via Tailwind CDN), and JavaScript live in `Home.html`. There is no build step, no package manager, and no bundler.
- **Styling:** Tailwind CSS loaded from CDN with a custom config block (`<script id="tailwind-config">`). The theme extends Material Design 3 color tokens mapped to ING's brand palette (primary orange: `#ff6200`).
- **Fonts:** Plus Jakarta Sans (headlines), Inter (body/labels), and Material Symbols Outlined — all loaded from Google Fonts CDN.
- **Navigation targets:** Most "Start creating" cards link to Adobe Experience / Workfront URLs with `target="_top"` so they break out of any parent iframe context.
- **Brief modal:** Card 3 ("Generate campaign concepts") opens a modal containing an embedded Workfront request form via `<iframe src="...workfront.com/requests/newRequestEmbedded?...&skipQssRedirect=true">`. On submission, a `postMessage` listener redirects `window.top` to the Workfront campaign dashboard.

## Key URLs (hardcoded)

- Workfront new-request project ID: `69b856480006ff3e3202f2e2613224b1`
- Workfront canvas dashboard ID: `69b9a4cc7937bb1878b7cce5`
- Adobe Experience tenant: `@accenture-partner/so:mrmworkfront-Production`

## Development

No build or install step — open `Home.html` directly in a browser or serve it with any static file server, e.g.:

```bash
npx serve .
# or
python -m http.server
```
