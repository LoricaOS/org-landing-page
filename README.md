# org-landing-page

The marketing landing page for **[AspisOS](https://github.com/AspisOS)** — served
at **[aspisos.org](https://aspisos.org)** via GitHub Pages.

Static HTML/CSS, no build step. Dark, monochrome design matching the AspisOS brand.

## Layout

```
index.html      the page (single file; all sections, screenshot placeholders inline)
style.css       the styling (dark, frosted-glass, responsive)
assets/         logo.png, wallpaper.png, favicon.png, icon-square.png
CNAME           the custom domain (aspisos.org)
.nojekyll       tells Pages to serve files verbatim (no Jekyll processing)
.github/workflows/deploy.yml   publishes the repo root to GitHub Pages on every push to main
```

## Screenshots

The page ships with **placeholder tiles** where real screenshots go. Each tile —
and an HTML comment right above it in `index.html` — describes exactly what to
capture and at what resolution. Search `index.html` for `SCREENSHOT:` to find them:

| id | what to show |
|----|--------------|
| `shot-desktop`  | hero: the live desktop — Lumen over the wallpaper, dock, top bar, overlapping frosted windows |
| `shot-apps`     | Files + Editor + Calculator together; frosted glass + accent theming |
| `shot-terminal` | the "money shot": `uid=0` yet a privileged syscall is DENIED (ENOCAP) |
| `shot-greeter`  | the Bastion greeter / boot |
| `shot-settings` | Settings → System (Edition: Community, Kernel version) |
| `shot-games`    | 2048 / Snake / Minesweeper |
| `shot-net`      | Feeds RSS reader or Lantern browser |

To swap one in: save the capture into `assets/` (e.g. `assets/shot-desktop.png`)
and replace that `<figure class="shot">…</figure>` with `<img class="shot" src="assets/shot-desktop.png" alt="…">`.

## Deploying

Pushing to `main` runs `.github/workflows/deploy.yml`, which publishes the repo
root to GitHub Pages. **One-time setup in repo Settings → Pages: set _Source_ to
_GitHub Actions_.** DNS for `aspisos.org` is configured separately (an `A`/`ALIAS`
to GitHub Pages plus a `CNAME` for `www`); the `CNAME` file here claims the domain.

## Local preview

```sh
python3 -m http.server 8000   # then open http://localhost:8000
```
