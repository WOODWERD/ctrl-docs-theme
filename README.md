# WOODWERD docs theme

WOODWERD Digital for every product's documentation site. It is a set of overrides for
[Material for MkDocs](https://squidfunk.github.io/mkdocs-material/): the toolkit strip, a
product header over a 2 px amber rule with no brand mark, warm cream pages in light and
warm near-black in dark, Inter and JetBrains Mono bundled with the site, and the WOODWERD
Design mark in the footer only.

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
     palette:
       - media: "(prefers-color-scheme)"
         primary: custom
         accent: custom
         toggle: { icon: material/monitor, name: "Theme: match my computer's setting" }
       - media: "(prefers-color-scheme: light)"
         scheme: default
         primary: custom
         accent: custom
         toggle: { icon: material/brightness-7, name: "Theme: light" }
       - media: "(prefers-color-scheme: dark)"
         scheme: slate
         primary: custom
         accent: custom
         toggle: { icon: material/brightness-4, name: "Theme: dark" }
   extra_css:
     - assets/woodwerd/woodwerd.css
   extra:
     purpose: One line on what the tool does, as it reads in the All tools menu.
     version: v0.1.0
   ```

   `repo_name` decides which entry in All tools is marked You are here.

3. Add `docs-theme/` to `.gitignore`. To preview locally, clone this repo into `docs-theme/`.

## What is in it

| Path | What |
| --- | --- |
| `overrides/main.html` | The toolkit strip and its All tools menu; turns off Google Fonts |
| `overrides/partials/header.html` | The product header, copied from Material 9.7.7. Recheck it when that pin moves |
| `overrides/partials/copyright.html` | Footer: WOODWERD mark, tagline, the site's copyright line |
| `overrides/partials/ww-mark.html` | The WOODWERD Design mark, inline, in `currentColor` for both themes |
| `overrides/assets/woodwerd/woodwerd.css` | WOODWERD Digital tokens, type, spacing and components |
| `overrides/assets/images/favicon.png`, `overrides/assets/woodwerd/favicon.svg`, `apple-touch-icon.png` | The WW button for browser tabs and home screens |
| `overrides/assets/woodwerd/fonts/` | Inter and JetBrains Mono with their OFL licences |

The menu's tool list repeats the one in ESP Ctrl, Cable Ctrl, File Ctrl, Box Ctrl and Tool Ctrl until the products
share tokens and chrome. Change them all together.

Light-mode links use a darker amber (`#8A5F22`) because the brand amber is too light for
text on cream.

## License

The theme code is MIT, © 2026 WOODWERD LLC. The WOODWERD name and marks are not covered
by the MIT license and may not be used to brand other projects.
