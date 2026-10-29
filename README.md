# WOODWERD docs theme

One look for every Ctrl product's documentation site. It is a set of overrides for
[Material for MkDocs](https://squidfunk.github.io/mkdocs-material/): the WOODWERD Design
mark in the header and footer, the ink header with an amber rule, warm cream pages, amber
links, Inter for text and JetBrains Mono for code, sharp corners, and a strip linking the
Ctrl family.

Change it here and every product site picks it up on its next build.

## Use it in a product repo

1. In the docs workflow, check this repo out next to the docs before `mkdocs build`:

   ```yaml
   - uses: actions/checkout@v4
     with:
       repository: WOODWERD/ctrl-docs-theme
       path: docs-theme
   ```

2. In `mkdocs.yml`:

   ```yaml
   theme:
     name: material
     custom_dir: docs-theme/overrides
     logo: assets/woodwerd/woodwerd-mark-light.svg
     font:
       text: Inter
       code: JetBrains Mono
     palette:
       - media: "(prefers-color-scheme: light)"
         scheme: default
         primary: custom
         accent: custom
         toggle: { icon: material/brightness-7, name: Dark mode }
       - media: "(prefers-color-scheme: dark)"
         scheme: slate
         primary: custom
         accent: custom
         toggle: { icon: material/brightness-4, name: Light mode }
   extra_css:
     - assets/woodwerd/woodwerd.css
   ```

3. Add `docs-theme/` to `.gitignore`. To preview locally, clone this repo into `docs-theme/`.

## What is in it

| Path | What |
| --- | --- |
| `overrides/main.html` | The Ctrl family strip above the header |
| `overrides/partials/copyright.html` | Footer: WOODWERD mark, tagline, the site's copyright line |
| `overrides/assets/woodwerd/woodwerd.css` | Colours, type, corners, tables, notes, buttons, footer |
| `overrides/assets/woodwerd/woodwerd-mark-light.svg` | The WOODWERD Design mark, cream, for dark grounds |
| `overrides/assets/woodwerd/woodwerd-mark-dark.svg` | The same mark in ink, for light grounds |

Text contrast is at least 4.5:1 in both schemes. Light-mode links use a darker amber
(`#8A5F22`) because the brand amber is too light for text on cream.

## License

The theme code is MIT, © 2026 WOODWERD LLC. The WOODWERD name and marks are not covered
by the MIT license and may not be used to brand other projects.
