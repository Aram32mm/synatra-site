# Source evidence

Reviewed October 27, 2026 (America/Los_Angeles). Read-only GitHub `main` archives; neither original checkout was changed.

- Frontend: `Aram32mm/synatra_frontend`, `8c5b610ad91f61346156743f2347f551cd951415`.
- Backend: `Aram32mm/synatra_backend`, `497a78b82a99aeddc6bc398ca9538d68a0221429`.

## Brand and illustrations

- Frontend `docs/brand/BRAND.md`: the approved Eight, palette, fatigue/recovery meanings and voice.
- `assets/mark-{light,dark}.svg` derive from `docs/brand/synatra-mark-on-{light,dark}.svg`. SVGO 4.1.0 removes metadata and optimizes markup without redrawing, recoloring or changing the composition.
- Frontend `docs/design/tokens.json`: page/surface/ink/accent/readiness colors, separately for light and dark appearances. At the owner’s request, body fills mix the original readiness blue (78%) or fatigue red (76%) with the surface color in OKLab; the large headline uses the deeper recovered-blue token. The mark remains unchanged. System fonts follow the explicit website brief, rather than downloading Sora.
- Hero silhouettes and muscle shapes derive from `docs/design/bodymap-v2.json`. Redundant points simplified with a 1.15-unit tolerance on the original 200 × 440 grid, then converted with the file's closed Catmull–Rom spline specification. Original mirroring rules retained. Both front and back shown; no new anatomy invented.
- `docs/design/bodymap-female.json` inspected as an alternative geometry; the initial landing illustration uses the original male body map. This is a nonpersonalized product illustration.
- Backend `src/main/kotlin/com/synatra/shared/MuscleTaxonomy.kt`: 22 muscle groups. Frontend `docs/WIRE_LEDGER.md` W41 explains why the 21-group figure has no separate traps shape.
- Frontend `docs/design/DESIGN_SYSTEM.md`: readiness, session, check-in, reps in reserve.
- PR #206 and `docs/listing/README.md`: approved App Store images and Watch interaction references. The website uses lightweight labeled mechanism illustrations, not the much larger listing images.
- All numerical examples are illustrative, not a personal training recommendation. The watch view is explicitly labeled as an illustration.

## Privacy and support

| Statement | Source in the reviewed snapshot |
| --- | --- |
| Account/profile fields, optional unused height, profile weight for starting loads | Backend `docs/modules/user.md:9–50` |
| Apple identities, sign-in restrictions and revocation before deletion | Backend `docs/modules/user.md`, Sign-in and Account deletion sections |
| Workouts, sets, load, reserve and session timestamps | Backend `docs/modules/session.md:11–29` |
| Readiness uses sets, time, sleep, illness, soreness; other recorded signals unused | Backend `docs/modules/recovery.md:214–241` |
| Phone reads sleep, resting HR, HRV and body mass with permission | Frontend `synatra_frontend/Synatra/HealthSync.swift:91–107` |
| Health originals are not erased by Synatra deletion | Frontend `synatra_frontend/Synatra/HealthSync.swift:73–78` |
| Watch heart-rate reads and workout writes | Frontend `docs/RELEASE.md:129–130` |
| Fly region `sjc` | Backend `fly.toml:5` |
| Neon database | Backend `docs/BACKEND_HANDOFF.md:5` |
| Nightly encrypted dumps; GitHub artifact retention 90 days | Backend `.github/workflows/backup.yml:53–78` |
| Permanent minimal deletion record and restoration procedure | Backend `docs/adr/0002-account-deletion-in-flight-events.md:131–139` |
| No tracking manifests / no analytics or ad SDKs | Frontend `docs/RELEASE.md:105–117` and app privacy manifests |
| Account deletion confirmation | Frontend `synatra_frontend/Synatra/Views/AccountActions.swift:60–71` |
| Apple-linked deletion is not wired into the reviewed phone build | Frontend `synatra_frontend/Synatra/ScreenModels/SettingsModel.swift:296–315` |
| Current email sign-in pending F10 | Frontend main commit #213; sign-in implementation and F10 planning document |
| Settings → Preferences → Units | Frontend `synatra_frontend/Synatra/Views/UnitsAndEffort.swift:5–23`, `SettingsView.swift:249–250` |
| Settings → Watch link → Push account to watch now | Frontend `synatra_frontend/Synatra/Views/SettingsDeviceSections.swift:49–56` |

The backend can store imported external activities, but current phone Health permissions do not include workout imports. The policy therefore does not claim that this feature is available in the reviewed release.

Repository configuration proves intended behavior, not provider deployment state. Unverified geographic locations, log retention, inactive-account retention, support retention, operator identity and external processing remain explicit owner notes. No blanket promise that all collected data feeds readiness is made.
