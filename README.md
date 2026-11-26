# specmint-site

Landing site for [specmint.ngvoicu.dev](https://specmint.ngvoicu.dev) — single static `index.html`, no build step. Remotes: `origin` = NAS, `upstream` = GitHub (Pages deploys from `main`).

## Fonts

DM Serif Display (regular and italic), DM Sans (300–700, regular and italic) and JetBrains Mono (400–500), all SIL OFL, are served from `fonts/` as WOFF2, with each licence beside them (`*-OFL.txt`). They are the files Google Fonts serves for the stylesheet the page used to load, `https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=DM+Sans:ital,opsz,wght@0,9..40,300..700;1,9..40,300..700&family=JetBrains+Mono:wght@400;500&display=swap` (DM Serif Display v17, DM Sans v17, JetBrains Mono v24): only its `latin` and `latin-ext` files, since the page shows no other script. DM Sans and JetBrains Mono are variable fonts, one file for every weight. The `<style>` block starts with their `@font-face` rules (Google's `unicode-range` and `font-display: swap`), and the head preloads `fonts/dm-sans-latin.woff2` and `fonts/dm-serif-display-latin.woff2`, the two the first screen needs. The page makes no request to Google.

To refresh them, ask Google for that stylesheet as a current browser does, then download the `latin` and `latin-ext` files it lists over the ones in `fonts/`, under the same names, and copy any changed `unicode-range` into the `@font-face` rules:

```bash
curl -s -A 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/131.0.0.0 Safari/537.36' \
  'https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=DM+Sans:ital,opsz,wght@0,9..40,300..700;1,9..40,300..700&family=JetBrains+Mono:wght@400;500&display=swap'
# each /* latin */ and /* latin-ext */ block names a https://fonts.gstatic.com/…woff2 file: curl -o fonts/<name>.woff2 <url>
```

The licences come from `github.com/google/fonts` (`ofl/<family>/OFL.txt`). A character outside Latin (Greek, Cyrillic, Vietnamese) would need that subset's file and rule added the same way.

## Deploying (read this — Pages builds get stuck)

Push `main` to `upstream` (GitHub) and Pages builds automatically — but builds **regularly hang in `"building"`**. After every push:

```bash
gh api repos/ngvoicu/specmint-site/pages/builds/latest --jq .status   # expect "built" within ~1 min
gh api -X POST repos/ngvoicu/specmint-site/pages/builds               # re-queue if it sits in "building"
```

Then confirm the change is actually live: `curl -s https://specmint.ngvoicu.dev/ | grep '<something-from-your-change>'`.
