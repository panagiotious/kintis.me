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
| `index.html` | The page: markup, styles, the script for the animated plot and the analytics events, all inline |
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

## Analytics

The page reports to [Umami Cloud](https://cloud.umami.is): cookieless, no consent banner, no stored IP addresses. The tracker tag is in `<head>`; the events come from the last `<script>` block in `index.html`, which does nothing when the tracker is blocked.

| Event | Fires when | Data |
| --- | --- | --- |
| pageview | page load (automatic) | referrer, country, device, browser, UTM tags |
| `outbound` | click on an external link | `url`, `section`, `kind` (`social`, `profile`, `publication`, `link`) |
| `email` | click on a `mailto:` link | `section` |
| `nav` | click on an in-page `#anchor` link | `target`, `section` |
| `field-select` | click on a field tag button | `field`, `section` |
| `section-view` | a section stays on screen for about a second | `section` |
| `engaged` | 15, 30, 60, 120 and 300 seconds of visible-tab time | `seconds` |

- **New links and sections are picked up automatically.** Links are classified by where they sit (`.social`, `.profiles`, `a.t`); sections are any `<section id>` inside `<main>`.
- **To add an event,** call `track('name', { key: 'value' })` inside that script block. Names are limited to 50 characters.
- **To keep your own visits out of the stats,** run `localStorage.setItem('umami.disabled', 1)` once in the browser console on kintis.me.
- **Only `kintis.me` reports** (`data-domains`), so local previews and the `github.io` URL stay out of the numbers.
- **To see where a shared link was clicked,** append UTM tags, for example `https://kintis.me/?utm_source=linkedin`.

## Notes

- Team and company logos are trademarks of their owners and are shown only to say what the author likes.
- The page loads the Lexend typeface from Google Fonts.
