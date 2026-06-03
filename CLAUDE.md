# CLAUDE.md

Guidance for AI agents working in **specmint-site** — the landing page for specmint.io.

## Knowledge base

Site purpose lives in the **ngvoicu-sme** brain. Read and write through kluris (never edit brain files by hand — the skill enforces an approval protocol):

- `/kluris-ngvoicu-sme` — Claude Code skill (search, learn, remember, create)
- `kluris search "<query>" --brain ngvoicu-sme` — direct search

## What this repo is

A static single-page landing page deployed at **specmint.io**. Built for SEO and link-sharing, **not** as a documentation site — actual docs live in each skill's `README.md` and `SKILL.md` (specmint-core, specmint-tdd).

## What's here

- `index.html` — single-page HTML with metadata, OG image, sitemap, webmanifest
- `CNAME` — points to specmint.io
- Standard PWA / icon set (favicon, apple-touch-icon, icon-192, icon-512)
- `og-image.png`, `robots.txt`, `sitemap.xml`

No JavaScript framework, no build step.

## What this repo is NOT

A documentation site. If a change feels like docs (workflow explanation, command reference, examples), it belongs in `specmint-core` or `specmint-tdd` instead.
