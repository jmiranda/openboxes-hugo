# OpenBoxes Website

Marketing/docs website for **OpenBoxes** — open-source supply chain & inventory
management software for healthcare and disaster relief. Built with **Hugo**
(static site generator), deployed on **Netlify**, content edited via **Netlify
CMS** (`/admin`) and historically **Forestry** (`.forestry/`).

## Running locally

```bash
./bin/hugo serve          # dev server with live reload at http://localhost:1313
./bin/hugo                # production build into ./public (gitignored)
```

⚠️ **Hugo version is pinned to 0.92.2** — this matters.
- Netlify builds with `HUGO_VERSION = "0.92.2"` (see `netlify.toml`).
- The site does **not** build on current Hugo (0.130+): it uses `.Site.Author`,
  `.Site.LanguageCode`, `.Site.DisqusShortname`, `.Site.GoogleAnalytics`, etc.,
  which were removed/deprecated. `brew install hugo` gives a broken-for-this-repo
  version.
- A matching pinned binary lives at `./bin/hugo` (gitignored). If it's missing,
  reinstall it:
  ```bash
  curl -sL https://github.com/gohugoio/hugo/releases/download/v0.92.2/hugo_extended_0.92.2_macOS-64bit.tar.gz \
    | tar xz -C bin hugo
  ```
  (swap the asset name for your OS/arch from the v0.92.2 release page.)
- Do **not** call a global `hugo` for this project unless you've confirmed it's 0.92.2.

## Layout / how the site is assembled

- `config.toml` — site config: menus (`[[menu.main]]`), `[params]`, per-section
  `enable` toggles (`[params.features]`, `[params.benefits]`, …), `[Permalinks]`.
- `content/` — page content (Markdown w/ TOML `+++` or YAML `---` front matter).
  - `content/blog/` — 48 posts (release notes + case studies). Permalink:
    `/blog/:year/:month/:day/:filename/` (set in `config.toml`). Date comes from
    front matter, **not** the filename.
  - `content/posts/` — Netlify CMS-created posts.
  - Most top-level pages (`features.md`, `about.md`, …) are thin stubs; their real
    content is assembled from `data/` + `layouts/partials/`.
- `data/<section>/*.yaml` — **the main content source for the homepage & feature
  pages.** Each file is one item; `weight` controls order. Sections:
  `features`, `benefits`, `carousel`, `categories`, `testimonials`, `partners`,
  `supporters`, `services`, `support`, `users`, `pricingfaqs`, `tutorials`.
  Example: to add a feature, drop a new `data/features/<slug>.yaml` (see
  `data/features/dashboard.yaml` for the schema: `weight`, `name`, `category`,
  `icon`, `description`, `items`, `docs`, `screenshots`).
- `layouts/` — **project overrides** of the theme (take precedence over
  `themes/`). `layouts/index.html` assembles the homepage from partials;
  `layouts/partials/*.html` render each section (most loop over `.Site.Data.<x>`).
- `themes/hugo-universal-theme/` — vendored theme (NOT a git submodule, so it's
  safe to edit directly; changes are committed to this repo).
- `static/` — assets served as-is: `css/`, `js/`, `img/`, `uploads/`,
  `_redirects` (Netlify), `admin/` (Netlify CMS config + entry point).

## Editing content — common tasks

- **Homepage section content** → edit `data/<section>/*.yaml`.
- **Look/markup of a section** → edit `layouts/partials/<section>.html`.
- **Turn a section on/off** → flip its `enable` under `[params.<section>]` in `config.toml`.
- **Nav menu** → `[[menu.main]]` entries in `config.toml` (uses `weight`, `parent`).
- **New blog post** → add `content/blog/<slug>.md` with `+++` front matter
  (`title`, `date`, `categories`, `tags`; see `.forestry/front_matter/templates/blog-post.yml`).
- After edits, `./bin/hugo serve` hot-reloads; verify the affected page in the browser.

## Deploy

Push to `master` → Netlify builds (`command = "hugo"`, `publish = "public"`,
`HUGO_VERSION = "0.92.2"`) and publishes to https://openboxes.com/.
