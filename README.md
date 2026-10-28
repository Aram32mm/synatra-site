# Synatra

Static marketing site for [synatra.watch](https://synatra.watch), by Tensional Labs. Plain HTML, CSS and SVG. No build step, runtime JavaScript, cookies, analytics, external fonts or external scripts.

## Preview

From this directory, run `python3 -m http.server 4173 --bind 127.0.0.1`, then open `http://127.0.0.1:4173`.

- `index.html`: landing page with a simulated recovery week and four CSS mechanism illustrations.
- `privacy.html`: source-based policy draft. Explicit `[OWNER: confirm]` notes must be resolved before release.
- `support.html`: source-verified help and account-deletion steps, with current release limitations marked.
- `404.html`, `robots.txt`, `sitemap.xml`, `CNAME`: hosting and discovery.
- `assets/`: local branding and stylesheet. Body-map SVG is inline in the landing page.
- `docs/`: source provenance, review evidence and launch handoff. Not published by the workflow.

## Review and deployment

Changes belong on feature branches and enter `main` through owner-reviewed pull requests. Never push site changes directly to `main`. GitHub Pages is configured for Actions and the custom domain `synatra.watch`.

After owner merge, `.github/workflows/pages.yml` stages only the public site files and deploys them. It also supports manual dispatch on `main`. No source or evidence directory is uploaded.

The App Store badge remains hidden until the owner supplies the approved destination. The site does not collect email or pretend to offer an available download.

See [launch handoff](docs/LAUNCH.md), [source evidence](docs/SOURCES.md), and [verification results](docs/VERIFICATION.md).
