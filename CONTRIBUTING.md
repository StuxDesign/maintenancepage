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

## Versioning and changelog

- The version lives in `VERSION.md` (a bare version string) — bump it on every release, following [Semantic Versioning](https://semver.org/)
- Every release gets a `CHANGELOG.md` entry using `###` subsections in this order: Added, Changed, Fixed, Removed, Security, Deprecated
- `commit.sh` (bash) and `commit.bat` (Windows) read `VERSION.md` to commit and tag a release — no need to edit them per release

## Before committing

- Open `index.html` in a browser and check it renders correctly
- Check the page at common viewport widths (mobile/tablet/desktop) since it's meant to be responsive
