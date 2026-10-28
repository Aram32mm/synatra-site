# Verification

October 27, 2026 (America/Los_Angeles), against a local HTTP server serving the final static files. Production DNS, TLS, caching and the deployment workflow have not been exercised; the owner has not merged the draft.

## Lighthouse 13.5.0

| Page | Mode | Performance | Accessibility | Best practices | SEO |
| --- | --- | --- | --- | --- | --- |
| Landing | Mobile | 100 | 100 | 100 | 100 |
| Landing | Desktop, 1440 px | 100 | 100 | 100 | 100 |
| Privacy | Mobile | 100 | 100 | 100 | 100 |
| Privacy | Desktop, 1440 px | 100 | 100 | 100 | 100 |
| Support | Mobile | 100 | 100 | 100 | 100 |
| Support | Desktop, 1440 px | 100 | 100 | 100 | 100 |

Raw reports: `evidence/lighthouse-{index,privacy,support}-{mobile,desktop}.json`. Summary: [lighthouse-summary.json](evidence/lighthouse-summary.json). Local-server caching, compression and small shared-style inefficiencies appear as non-score-blocking opportunities. No claim is made about production scores.

## HTML and browser checks

- `html-validate` 11.17.0, `html-validate:standard`: all four HTML documents pass with zero diagnostics. [Raw result](evidence/html-validation.json), an empty diagnostics array. The SVG focusable lint rule is disabled; hero illustrations are explicitly hidden from assistive technology and the explanatory chart has an accessible title.
- Eighteen page/theme/width combinations: 3 pages × light/dark × 360/390/1440 px. No horizontal overflow, page errors or externally loaded resources.
- Reduced motion: zero running animations. Pause and resume: pass. FAQ expand/collapse: pass. The animation toggle is also removed from focus order when reduced motion disables all motion.
- Dark-mode axe-core 4.14.0, WCAG A/AA and 2.1 A/AA: no reported violations across the three pages. Landing's animated/hidden content retains one automated contrast item requiring manual review; this is recorded as incomplete, not silently counted as a pass. Screenshots were visually reviewed.
- Local navigation and asset targets resolve; sitemap XML parses; no script elements. The 404 document renders, though Python's static server does not implement GitHub Pages' custom 404 routing.
- Hero figure markup plus the entire shared stylesheet totals 59,797 bytes, below 60,000 bytes. No canvas, JavaScript, webfonts or animation library.

[Browser results](evidence/browser-checks.json) · [Dark-mode accessibility results](evidence/dark-accessibility.json)

## Screenshots

All full-page screenshots below use reduced motion for deterministic comparison. Additional animation frames show independent regional fatigue and recovery. Phone screenshots are 390 px; desktop screenshots are 1440 px. The 360 px layouts were checked separately.

| Page | Phone light | Phone dark | Desktop light | Desktop dark |
| --- | --- | --- | --- | --- |
| Landing | [390 light](evidence/index-390-light.png) | [390 dark](evidence/index-390-dark.png) | [1440 light](evidence/index-1440-light.png) | [1440 dark](evidence/index-1440-dark.png) |
| Privacy | [390 light](evidence/privacy-390-light.png) | [390 dark](evidence/privacy-390-dark.png) | [1440 light](evidence/privacy-1440-light.png) | [1440 dark](evidence/privacy-1440-dark.png) |
| Support | [390 light](evidence/support-390-light.png) | [390 dark](evidence/support-390-dark.png) | [1440 light](evidence/support-1440-light.png) | [1440 dark](evidence/support-1440-dark.png) |

[Chest focus](evidence/animation-monday.png) · [Arms focus](evidence/animation-thursday.png) · [Lower-leg focus](evidence/animation-sunday.png)

The 21-second hero cycle shifts focus every three seconds across chest, back, shoulders, arms, core, upper legs and lower legs. Each region fatigues and recovers on its own offset; the whole figure never changes to one readiness state. Mirrored muscles share the same phase. The caption identifies the active region rather than displaying an aggregate percentage. Reduced motion shows a static chest-focused example. This sequence is illustrative, not engine output or a training recommendation.

October 28 update: 42 half-second samples across the complete loop confirmed independently colored regions; see [regional-animation.json](evidence/regional-animation.json). Layout, pause/resume, reduced-motion, HTML and dark accessibility checks were rerun. Landing Lighthouse reports were refreshed; other page reports are from October 27.
