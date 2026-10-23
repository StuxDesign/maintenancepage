<p align="center">
  <picture><source media="(prefers-color-scheme: dark)" srcset="https://global.media.stux.design/logo-light.png"><source media="(prefers-color-scheme: light)" srcset="https://global.media.stux.design/logo-dark.png"><img src="https://global.media.stux.design/logo-dark.png" height="80" alt="Stux.Design Logo"></picture>
</p>

# Contributing to Maintenance Page

This is a single-file HTML template, open for use and modification per the
[License](README.md#license) section. This document is for anyone working on
the template itself (not a downstream deployment).

## Local setup

There's no build step or dependencies — just clone the repo and run
`./dev-server.sh [port] [--no-dev-mode]` (or `dev-server.bat` on Windows), then open
`http://127.0.0.1:8000`. PHP (7.4, like the other Stux projects) is only the local web
server: `.github/dev-router.php` serves the folder the way GitHub Pages does and, with
DEV_MODE on (the default), answers `assets/dev-mode.js` with `window.SITE_DEV_MODE = true`
so the dev banner shows. Production serves the committed `assets/dev-mode.js`, which
leaves it off.

## Project conventions

- Static HTML pages (`index.html`, `legal.html` + `legal/`, `changelog.html`, `404.html`) — no framework, no build step, no backend.
- The sitemap (`sitemap.xml`, `sitemap/index.html`, `robots.txt`) is generated: after adding or removing a page, edit the `PAGES` list in `scripts/build-sitemap.py` and run `python scripts/build-sitemap.py`, then commit the result
- Keep it lightweight and dependency-free; Gontserrat and Creato Display are self-hosted under `assets/fonts/`, like the other Stux.Group page templates, not pulled from a third-party CDN.
- `changelog.html` fetches and renders `CHANGELOG.md` at runtime — don't hand-duplicate changelog content into it.
- General contact uses `hello@stux.design`; legal-page contact uses `legal@stux.design`.
- The Stux.Design twist is the artboard block at the end of the `<style>` in `index.html`
  (`.artboard`, `.ruler`, `.selection`, `.sel-tag`, `.crop`): keep it to the main page, and keep the
  selection box around the headline's highlighted words.
- Match the existing code style: no comments explaining *what* the markup does, only *why* when something is genuinely non-obvious.

## Icons and link previews

The icon tags and the Discord link preview in each page's `<head>` (between the `BEGIN head tags` / `END head tags` comments) are generated: edit `scripts/build-head-tags.py` (add new pages to its `PAGES` list too; `build-sitemap.py` runs it for you) and run `python scripts/build-head-tags.py`. The icons themselves are `favicon.ico`, `apple-touch-icon.png`, `site.webmanifest` and `assets/icon-*.png`, made from the Stux.Design icon.

## Tests

Run `bash tests/run.sh` before every release. It needs Python 3 (and PHP 7.4 for the dev-server checks, which are skipped without it). It checks the version (`tests/version.sh`), that every page's Discord preview is valid, under 3,000 bytes and up to date (and that the 404 page has none), and that the icon set is complete and every page's `<head>` lists it.

## Versioning

This project uses [Date Versioning](https://datevers.ing). To release:

1. Add a `## vYY.MM.DD` entry at the top of `CHANGELOG.md`, with its sections in this order: Added, Changed, Fixed, Removed, Security, Deprecated.
2. Set `VERSION.md` to the same bare version (no `v`): today's **UTC** date as `YY.MM.DD`, or `YY.MM.DD-1`, `-2`… for later releases the same UTC day. Never a future date. Use UTC, not local time: just after midnight in the UK it is still the previous day in UTC.
3. Run `bash tests/run.sh` (it includes `tests/version.sh`).
4. Run `./commit.sh` (or `commit.bat` on Windows). It checks the version, commits and tags `vYY.MM.DD`, and never pushes.

## Before committing

- Open `index.html` in a browser and check it renders correctly
- Check the page at common viewport widths (mobile/tablet/desktop) since it's meant to be responsive
