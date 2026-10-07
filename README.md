# kintis.me

Personal website of Panagiotis Kintis, PhD. One static page, no build step, served by GitHub Pages.

## Quick Start

Open `index.html` in a browser. That is the whole site.

To serve it locally the way GitHub Pages does:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

To publish a change, commit it to `main` and push. GitHub Pages rebuilds within a minute or two.

## Layout

| Path | What it is |
| --- | --- |
| `index.html` | The page: markup, styles and the script for the animated plot, all inline |
| `assets/portrait-square.jpg` | Portrait at the top of the page |
| `assets/playful-solo.jpg` | Photo in the Background section |
| `assets/logos/` | Logos in the "Things I like" section |
| `assets/favicon.svg`, `assets/apple-touch-icon.png` | Browser tab icon and iOS home-screen icon |
| `CNAME` | Custom domain for GitHub Pages |
| `.nojekyll` | Tells GitHub Pages to serve the files as they are |

## How to extend it

- **Text and sections:** everything is in `index.html`. Each section is a `<section>` with an `id` that the navigation links point at.
- **Styles:** in the `<style>` block at the top of `index.html`. Colors are CSS variables on `:root`. The breakpoints are 1240, 1100, 960, 860, 520, 400 and 350 pixels.
- **The animated plot:** the script at the bottom of `index.html`. The three fields and their colors are in the `F` array; cluster positions are in `BASE`; cycle timing is `CYCLE`, `HOLD0` and `HOLD1`.
- **Logos:** add the file to `assets/logos/` and an `<li><img></li>` to the `.teams` list. The row never wraps; logos shrink to fit narrow screens.
- **Asset paths are relative** on purpose, so the page also works under a sub-path such as `https://<user>.github.io/kintis.me/`.

## Notes

- Team and company logos are trademarks of their owners and are shown only to say what the author likes.
- The page loads the Lexend typeface from Google Fonts.
