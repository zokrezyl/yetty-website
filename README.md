# yetty.ch — marketing website

The public marketing site for **yetty**, the GPU-accelerated *Terminal
Unchained*. Static, dependency-free, built to look good on everything from a
phone to a wide desktop.

## Structure

```
website/
  index.html        # single-page landing site
  css/style.css     # brand-palette styling, responsive, card-based layout
  js/main.js        # nav, mobile menu, scroll-reveal (no dependencies)
  assets/           # logo, favicon, mascot, OG cover (all SVG)
  CNAME             # custom domain: yetty.ch
  .nojekyll         # serve files as-is
.github/workflows/
  deploy.yml        # publishes website/ to GitHub Pages on a release tag
```

## Local preview

No build step — it's plain HTML/CSS/JS. Serve the folder with anything:

```sh
cd website && python3 -m http.server 8080
# then open http://localhost:8080
```

## Deployment

Deployment is **release-driven**. `.github/workflows/deploy.yml` runs only when
a version tag of the form `yetty-website-X.Y.Z` is pushed; it uploads the
`website/` directory as the GitHub Pages artifact and deploys it. The custom
domain `yetty.ch` is set via `website/CNAME`.

Cut a release:

```sh
git tag yetty-website-1.0.0
git push origin yetty-website-1.0.0
```

(The workflow can also be run by hand from the Actions tab via
**Run workflow** / `workflow_dispatch`.)

One-time setup in the repo settings: **Settings → Pages → Build and
deployment → Source: GitHub Actions**, then point the `yetty.ch` DNS at GitHub
Pages.

## Design

Colours come from the yetty brand palette only — a near-black blue/teal
background ladder with a mint accent (`#6BA892` / `#74C5A5`). No off-brand
hues are introduced.
