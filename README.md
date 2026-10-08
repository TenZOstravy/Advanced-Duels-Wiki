# Advanced Duels Wiki

Documentation website for the **Advanced Duels** Minecraft plugin, built with [MkDocs](https://www.mkdocs.org/) and the [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) theme.

## Requirements

- Python 3.9+
- pip

## Install dependencies

```bash
pip install mkdocs mkdocs-material
```

## Run locally (live preview)

```bash
mkdocs serve
```

Then open http://127.0.0.1:8000 in your browser. Pages reload automatically when you edit Markdown files.

## Build static site

```bash
mkdocs build
```

The static site is generated into the `site/` directory.

## Deploy to GitHub Pages

```bash
mkdocs gh-deploy
```

This builds the site and pushes it to the `gh-pages` branch of your repository. Enable GitHub Pages (Deploy from a branch → `gh-pages`) in the repository settings afterwards.

## Adding screenshots / GIFs

Place image files in `docs/assets/images/` and recordings in `docs/assets/gifs/`, then uncomment the matching line under each placeholder, for example:

```md
<!-- ![Duel GUI](assets/images/duel-menu.png) -->
```

becomes:

```md
![Duel GUI](assets/images/duel-menu.png)
```

## Project layout

```text
mkdocs.yml            # site configuration + navigation
docs/
  index.md            # homepage
  getting-started/    # installation, first setup
  configuration/      # config reference, languages
  arenas/             # arena creation, regeneration
  kits.md / duels/ / queue.md / spectating.md
  commands/           # player + admin command reference
  permissions.md / placeholders.md / guis.md
  integrations.md / data.md
  faq.md / troubleshooting.md / changelog.md / api.md
  assets/images/      # screenshots (added separately)
  assets/gifs/        # recordings (added separately)
```
