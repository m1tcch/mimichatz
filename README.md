# mimichatz

Blog documenting threat research, interesting projects and tooling. Built with
[Jekyll](https://jekyllrb.com/) and the
[Hydejack](https://hydejack.com/) theme (free starter kit), deployed to GitHub
Pages on a custom domain.

## Layout

```
_config.yml            site settings — title, menu, accent color, Hydejack options
_posts/                blog posts — YYYY-MM-DD-title.md
_featured_categories/  categories with their own sidebar-linked pages
_data/authors.yml      author box, sidebar social icons
about.md               about page
index.html             home page (blog layout)
posts.md               archive of all posts grouped by year
assets/img/            logo, sidebar background
docs/, example/        Hydejack's own docs + demo content — delete when done
.github/workflows/     GitHub Actions build + deploy to Pages
CNAME                  custom domain
```

## Writing a post

Create `_posts/YYYY-MM-DD-my-title.md`:

```yaml
---
layout: post
title: my post title
description: >
  One-line summary for cards, feeds and search results.
categories: [threat-research]   # or tooling / projects
tags: [malware, windows]
---
```

Markdown below the front matter. Posts in a featured category appear on that
category's page (e.g. `/threat-research/`), linked from the sidebar.

## Run locally

Full setup and troubleshooting: **[LOCAL-SETUP.md](LOCAL-SETUP.md)**. Short
version (requires Ruby 3.3 + DevKit and Bundler):

```bash
bundle install
```

```bash
bundle exec jekyll serve --livereload
```

Site serves at <http://localhost:4000> and rebuilds on save. Search is
disabled locally by default; set `JEKYLL_ENV=production` to enable it.

## Deploy

The theme is gem-based (Jekyll 4.x), which the legacy GitHub Pages pipeline
doesn't support — so the site builds via GitHub Actions
(`.github/workflows/pages.yml`):

1. Push this repo to GitHub, default branch `main`.
2. Repo → **Settings → Pages** → Source: **GitHub Actions**.
3. Custom domain: `CNAME` contains `mimichatz.com` — **edit it if your domain
   differs**, and keep `url:` in `_config.yml` in sync.
4. At your DNS provider:
   - Apex (`mimichatz.com`): `A` records → `185.199.108.153`,
     `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - `www`: `CNAME` record → `<username>.github.io`
5. In **Settings → Pages** enter the custom domain and tick **Enforce HTTPS**
   once the certificate issues.

Every push to `main` rebuilds and deploys.

## Upgrading to Hydejack PRO

If you buy [Hydejack PRO](https://hydejack.com/download/), swap the theme gem
in the `Gemfile` per the [deploy docs](https://hydejack.com/docs/deploy/) —
the content and config here carry over. PRO adds dark mode, the resume and
projects layouts, forms, and grid view.
