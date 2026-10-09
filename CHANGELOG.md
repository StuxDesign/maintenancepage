# Changelog

All notable changes to Maintenancepage are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/) (MAJOR.MINOR.PATCH).

## v1.0.3

### Changed

- The favicon follows the browser's light or dark theme: the deep icon (`icon-dark.png`) on light and the bright one (`icon-light.png`) on dark, straight from the brand's media host, so a brand colour change is just a new file there
- The logos and icons in the Markdown docs (README and the like) follow GitHub's light or dark theme, using each brand's `logo-light`/`logo-dark` and `icon-light`/`icon-dark` files

## v1.0.2

### Changed

- The favicon follows the browser's light or dark theme: the deep icon (`icon-dark.png`) on light and the bright one (`icon-light.png`) on dark, straight from the brand's media host, so a brand colour change is just a new file there
- The logos and icons in the Markdown docs (README and the like) follow GitHub's light or dark theme, using each brand's `logo-light`/`logo-dark` and `icon-light`/`icon-dark` files

## v1.0.1

### Added

- The home page's footer has a copyright line ("© 2026 Stux.Design. All rights reserved."), like the legal pages, with the years kept current automatically

### Fixed

- The legal, changelog and sitemap footers name Stux.Design in the copyright line instead of Stux.Group, and no longer say Stux.Design is operated by Stux Group Ltd: that belongs on the Imprint only, which still says it

## v1.0.0

### Added

- The maintenance page for Stux.Design (maintenancepage.stux.design), built like the other Stux.Group page templates in Stux.Design magenta (`#e71081`), with light and dark themes
- The Stux.Design artboard: the page sits on a faint layout grid with rulers along the top and left edges, the headline's highlighted words get a selection box with handles and a "Redrawing" tag, and the card has crop marks at its corners
- The Boring Legal Stuff hub with its six pages, a changelog page that renders `CHANGELOG.md`, a sitemap and a 404 page
- `dev-server.sh`/`.bat` that serve the site the way GitHub Pages does with DEV_MODE on (dev banner), and `--no-dev-mode` to see it as production does
