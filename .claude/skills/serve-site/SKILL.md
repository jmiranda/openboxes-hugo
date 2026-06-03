---
name: serve-site
description: Build and serve the OpenBoxes Hugo website locally. Use when asked to run, serve, preview, build, or screenshot this site, or to verify a content/layout change in the browser.
---

# Serve the OpenBoxes website

This is a **Hugo** static site pinned to **Hugo 0.92.2**. It does NOT build on
current Hugo — use the project-local pinned binary at `./bin/hugo`.

## Run the dev server

```bash
./bin/hugo serve          # http://localhost:1313 with live reload
```

To verify it's up (run server in background, then check):
```bash
curl -s -o /dev/null -w '%{http_code}\n' http://localhost:1313/
```
Expect `200`. Key pages: `/`, `/features/`, blog posts at
`/blog/:year/:month/:day/:slug/`.

## Production build

```bash
./bin/hugo                # outputs to ./public (gitignored)
```

## If `./bin/hugo` is missing

Reinstall the pinned binary (macOS x86 example; pick the right asset for the OS):
```bash
mkdir -p bin && curl -sL \
  https://github.com/gohugoio/hugo/releases/download/v0.92.2/hugo_extended_0.92.2_macOS-64bit.tar.gz \
  | tar xz -C bin hugo
```

## Gotchas

- A global `hugo` (e.g. from `brew install hugo`) is likely a newer version and
  **breaks this build** (`.Site.Author`, `.Site.LanguageCode`, etc. were removed).
  Always invoke `./bin/hugo`.
- `hugo --quiet` hides render errors and can exit 0 on a broken build. Use
  `./bin/hugo serve` or plain `./bin/hugo` to see real errors.
- Homepage/feature content comes from `data/*.yaml`, not the `.md` stubs — see
  `CLAUDE.md` for the content map.
