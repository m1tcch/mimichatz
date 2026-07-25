# Running mimichatz locally

Quick reference for building and previewing the site on your own machine.

## 1. One-time setup

The site needs **Ruby 3.3 with DevKit** and **Bundler**.

> Already done on this machine (2026-07-25): Ruby 3.3.11 is installed at
> `C:\Ruby33-x64` and all gems are installed. Skip to
> [Serve the site](#3-serve-the-site) — just open a **new** terminal first so
> it picks up Ruby on PATH.

On a fresh Windows machine:

```bash
winget install RubyInstallerTeam.RubyWithDevKit.3.3
```

Then open a **new** terminal (so PATH refreshes) and finish the DevKit setup:

```bash
ridk install 3
```

(Option 3 installs the MSYS2 development toolchain, needed to compile native
gems like `wdm`.)

Install Bundler:

```bash
gem install bundler
```

On macOS/Linux, install Ruby 3.3 via [rbenv](https://github.com/rbenv/rbenv)
or your package manager instead — everything else is the same.

## 2. Install the site's gems

From the repo root (where `Gemfile` lives):

```bash
bundle install
```

Re-run this whenever the `Gemfile` changes.

## 3. Serve the site

```bash
bundle exec jekyll serve --livereload
```

Then browse to <http://localhost:4000>. Pages rebuild automatically when you
save a file — `--livereload` also refreshes the browser for you.

Notes:

- **Changes to `_config.yml` are not picked up by the watcher** — stop the
  server (`Ctrl+C`) and start it again.
- Hydejack's search is disabled in local development to speed up builds.
  To test it, run in production mode:

  ```bash
  $env:JEKYLL_ENV="production"; bundle exec jekyll serve
  ```

## 4. Build only (no server)

```bash
bundle exec jekyll build
```

Static output lands in `_site/` (git-ignored). This is exactly what the
GitHub Actions workflow runs on deploy.

## Troubleshooting

| Symptom | Fix |
|---|---|
| `bundle: The term 'bundle' is not recognized` | Ruby isn't on PATH — open a new terminal, or install Ruby (step 1). |
| `Liquid Exception: undefined method '[]' for nil ... last-modified-at` | The `jekyll-last-modified-at` plugin reads dates from git. Make sure files are committed (`git add -A && git commit`). |
| Native gem build errors during `bundle install` | DevKit missing — run `ridk install 3` and retry. |
| Port 4000 already in use | `bundle exec jekyll serve --port 4001` |
