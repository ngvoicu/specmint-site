# CLAUDE.md

Guidance for AI agents working in **specmint-site** — the landing page for specmint.ngvoicu.dev.

## Knowledge base

Site purpose lives in the **ngvoicu-sme** brain. Read and write through kluris (never edit brain files by hand — the skill enforces an approval protocol):

- `/kluris-ngvoicu-sme` — Claude Code skill (search, learn, remember, create)
- `kluris search "<query>" --brain ngvoicu-sme` — direct search

## What this repo is

A static single-page landing page deployed at **specmint.ngvoicu.dev**. Built for SEO and link-sharing, **not** as a documentation site — actual docs live in each skill's `README.md` and `SKILL.md` (specmint-core, specmint-tdd).

## What's here

- `index.html` — single-page HTML with metadata, OG image, sitemap, webmanifest
- `CNAME` — points to specmint.ngvoicu.dev
- Standard PWA / icon set (favicon, apple-touch-icon, icon-192, icon-512)
- `og-image.png`, `robots.txt` (content signals: search, ai-input and ai-train all yes), `sitemap.xml` (the URL only: no `lastmod` to keep true)
- `llms.txt` — for AI agents: the hero's lede, the install commands as the page gives them, links to the four skill repositories; keep it in step with the page
- `fonts/` — DM Serif Display, DM Sans and JetBrains Mono as WOFF2 with their OFL licences, served from the site (no request to Google); `README.md`'s "Fonts" says where they came from and how to refresh them
- `logo.webp` (92×101) and `kluris-logo.webp` (92×92) — twice the largest size the page draws them at (46px); the full-size Specmint source is `logo.pxd`
- `preview-core-html.webp` and `preview-tdd-html.webp` (1404 wide, near-lossless WebP) — the gallery's previews, twice the widest the page draws them (702px, one column at 768 wide); each card links its full-size PNG (`preview-*-html.png`), which only a click loads

No JavaScript framework, no build step.

## What this repo is NOT

A documentation site. If a change feels like docs (workflow explanation, command reference, examples), it belongs in `specmint-core` or `specmint-tdd` instead.
