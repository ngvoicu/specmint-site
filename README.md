# specmint-site

Landing site for [specmint.ngvoicu.dev](https://specmint.ngvoicu.dev) — single static `index.html`, no build step. Remotes: `origin` = NAS, `upstream` = GitHub (Pages deploys from `main`).

## Deploying (read this — Pages builds get stuck)

Push `main` to `upstream` (GitHub) and Pages builds automatically — but builds **regularly hang in `"building"`**. After every push:

```bash
gh api repos/ngvoicu/specmint-site/pages/builds/latest --jq .status   # expect "built" within ~1 min
gh api -X POST repos/ngvoicu/specmint-site/pages/builds               # re-queue if it sits in "building"
```

Then confirm the change is actually live: `curl -s https://specmint.ngvoicu.dev/ | grep '<something-from-your-change>'`.
