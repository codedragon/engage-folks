# Creating an Engaging Presentation

By Maria Mckinley.

- [Project repository](https://github.com/codedragon/engage-folks)
- [Slide source on main](https://github.com/codedragon/engage-folks/blob/main/slides.md)

This presentation builds on the
[MaptimeCalgary presentation example](https://github.com/MaptimeCalgary/presentation-example)
and uses Reveal.js 3.0.0. Reveal.js is bundled in `bower_components/reveal.js`, so
no Bower installation is needed to preview the slides.

## Local preview and slide style

From the repository root, compile the Newspaperrock theme with [Sass](https://sass-lang.com/)
(Node.js and npm are required; `npx` downloads Sass without a global installation):

```bash
npx --yes sass@1 --no-source-map theme/source/newspaperrock.scss theme/newspaperrock.css
```

To automatically compile style changes, leave this running in one terminal:

```bash
npx --yes sass@1 --no-source-map --watch theme/source/newspaperrock.scss:theme/newspaperrock.css
```

In a second terminal, serve the repository locally with Python 3:

```bash
python3 -m http.server 8000 --bind 127.0.0.1
```

Open <http://127.0.0.1:8000/> and refresh after saving changes. Edit `slides.md`
for slide content and `theme/source/newspaperrock.scss` for styles, not the generated
`theme/newspaperrock.css`. Press Ctrl+C to stop the watcher or server.

The background uses `theme/Newspaperrock.jpeg`, centered and scaled to cover the
screen. A white overlay keeps the dark text readable. Adjust
`$backgroundOverlayOpacity: 0.6;` near the top of the Sass source: lower values show
more of the image, and higher values make the image subtler (`0` is clear, `1` is white).
Slides with an explicit Markdown `data-background` still override the theme background.
The Newspaperrock background photograph was taken by Maria Mckinley.

The new theme preserves the original fonts, colors, and Reveal.js base rules. Its
Sass source uses `@use "sass:color"` and `color.adjust` instead of deprecated Sass
imports and `lighten`/`darken`. Google Fonts `@import url(...)` rules are ordinary
CSS imports, not deprecated Sass imports. The original `maptimecalgary.scss` and
`maptimecalgary.css` remain unchanged; compiling the legacy source can still produce
its original deprecation warnings.

## Publishing

A published presentation URL has not been verified. Use the local preview above;
GitHub Pages deployment is a separate setup step. The repository and slide-source
links will show these files after they are pushed to `main`.

## License and credits

This project's original work is licensed under GPLv3; see [LICENSE](LICENSE).
Borrowed code retains its upstream MIT notices, including the MaptimeCalgary theme
and [Reveal.js](bower_components/reveal.js/LICENSE). The new theme preserves the
Reveal.js notice in both its Sass source and generated CSS. Bundled fonts retain
their own license files under `bower_components/reveal.js/lib/font/`.
Background photograph: Maria Mckinley (`theme/Newspaperrock.jpeg`).
The project license does not establish usage rights for third-party images.
