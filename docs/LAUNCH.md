# Launch handoff

All three requested pages are built in the draft PR. The owner remains the merger. Do not publish the policy draft with unresolved owner notes.

## Owner review

1. Review the landing design in both themes and at mobile/desktop widths.
2. Supply the approved App Store link when available; the badge is deliberately hidden.
3. Confirm Tensional Labs' legal identity/contact address, policy effective date, privacy practices outside these repositories, support mailbox readiness and intended account/support retention.

## For the lead, through the owner

- Confirm the released iPhone app's sign-in method. Current `main` still uses email; the backend supports Apple.
- Complete or verify fresh Apple authorization for deleting an Apple-linked account. `SettingsModel` currently cannot supply it; the backend correctly refuses deletion without it.
- Confirm Neon region, provider/log retention, deployed backup schedule and 90-day artifact retention, and the restoration procedure that preserves deletion records.
- DNS queries for `synatra.watch` A/CNAME and `www.synatra.watch` CNAME returned no answers during preparation. No DNS registrar is connected to this task, so DNS has not been changed.
- Repository Pages is already set to `build_type: workflow` and custom domain `synatra.watch`. HTTPS enforcement is currently false because no certificate has been issued. After DNS resolves and GitHub provisions a certificate, enable Enforce HTTPS and verify it.

GitHub's [custom-domain instructions](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site) list these apex A records:

| Host | Type | Value |
| --- | --- | --- |
| @ | A | 185.199.108.153 |
| @ | A | 185.199.109.153 |
| @ | A | 185.199.110.153 |
| @ | A | 185.199.111.153 |
| www | CNAME | aram32mm.github.io |

After the owner approves and merges, the Pages workflow deploys the static files. Verify the custom-domain HTTPS response, internal links and actual 404 response, then repeat Lighthouse against production because local results do not measure production DNS, caching or TLS.

Workflow follows GitHub's [static-site starter](https://github.com/actions/starter-workflows/blob/main/pages/static.yml), with an allowlisted staging directory so docs and evidence are not published.
