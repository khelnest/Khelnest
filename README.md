# KhelNest Website

Official domain: `https://khelnest.in`.

This repository contains only the static website, public game previews, policy
drafts and fonts. It must not contain app build configs, passwords, Firebase
service-account credentials, signing keys, account exports or private backups.

## Pages

- Home: `/`
- Privacy: `/privacy/`
- Terms: `/terms/`
- Account deletion: `/delete-account/`
- Reward rules: `/reward-rules/`
- Contact: `/contact/`
- Invitation fallback: `/invite/`

Contact and deletion actions open an email composer. No form claims a successful
submission without a backend. The site does not collect analytics or request ads.

The app is in development. The linked policy drafts explicitly disclose the
unresolved deletion, retention and reward-eligibility requirements; publishing
the website does not resolve them or establish Google Play approval.

## GitHub Pages

In repository Settings, Pages, select Deploy from a branch, `main`, `/ (root)`.
Set custom domain `khelnest.in` and enforce HTTPS once its certificate is issued.
The `CNAME` file matches that domain. Domain DNS and repository Pages settings
must be configured separately; a Git push is not proof of a working domain.

The `.well-known/assetlinks.json` file includes the current local KhelNest
certificate only. Add the actual Play App Signing SHA-256 certificate when
available before relying on App Links for Play-installed apps. Do not replace
the package name or generate a new upload key for routine updates.

## Content Maintenance

Website pages are generated in the app workspace using its shared legal source
and `tool/export_legal_pages.dart`; captured game previews contain no real user
information. Preserve the font license beside the bundled fonts.

Before a public or closed-test rollout, verify account/auth/provider deletion,
retention durations, support response handling, eligible countries, payout rules,
and current policies. Regenerate the pages after any behavior or wording change.