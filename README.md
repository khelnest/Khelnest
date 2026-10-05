# KhelNest Website

Official domain: `https://khelnest.in`.

This repository contains only the static website, compact game previews, policy
pages and fonts. It must not contain app build configs, passwords, Firebase
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

The pages use dated, structured disclosures and section navigation.
They still disclose incomplete deletion, retention and reward-eligibility
requirements. Website publication is not Google Play approval or proof that
those implementation requirements have been resolved. The Google Play links
open the listing for com.khelnest.app; availability depends on track access
and country, so the website does not claim universal download availability.

## Vercel Deployment

Import this repository with framework preset Other, root directory at the
repository root, empty build/install commands, and output directory `.`.
No environment variables or secret keys are required. The root-relative page
and asset URLs require serving the repository root over HTTP/HTTPS.

The checked-in vercel.json fixes these static build settings. Keep the Vercel
Git integration connected to khelnest/Khelnest, with Production Branch main
and Root Directory at the repository root. Do not disable deployments with an
Ignored Build Step. Pushes to main trigger production deployment; other branches
can produce previews using the project's normal integration settings.

After each push, verify the commit SHA in GitHub's deployment status or Vercel
Deployments, then check the actual production domain. An unchanged page alone
does not establish a failed auto-deploy system. Git acceptance and successful
production deployment are separate checks.

On 5 October 2026, commit `6f3032e` was pushed and GitHub reported a successful
Vercel production deployment. The live contact/privacy pages, App Links JSON and
new logo matched the local files over HTTPS. Later privacy-copy updates correct
Google-only user login and explain the signed-in payout-proof feed and optional
WhatsApp handoff; check the newest deployment after each subsequent push.

## Updating From The App Workspace

Generate the public website from the user-app directory:

```sh
dart run tool/export_legal_pages.dart
dart run tool/export_legal_pages.dart --check
git -C web/khelnest status --short
```

The website directory is the Git checkout; do not push the parent app workspace.
Review and commit only the website changes, then push main with an account that
has permission to this repository. Authentication must use the local GitHub
credential manager or CLI sign-in, not tokens in source, URLs or chat. No separate
GitHub Actions deployment or Vercel token is needed for the Git integration.

Current mobile layout has at least 44px navigation targets, 48px primary actions,
single-column small-screen content, compact previews and collapsible policy
contents. Policy text and account-deletion links remain available without JS.
The current KhelNest logo is used in navigation, the favicon and social previews.
The contact page also links the official WhatsApp channel for optional updates;
account and payment support remains a separate email route.
The current currency label is NestCoin. The app uses a local joined checkbox
confirmation to stop channel reminders; until confirmed, reminders are spaced
at least 24 hours apart on eligible Home visits/app resumes. No WhatsApp API is
used and opening a link is not proof of joining.

Configure khelnest.in and www.khelnest.in in Vercel, using the DNS values shown
for that project; redirect www to the apex. The CNAME and .nojekyll files are
legacy GitHub Pages metadata and do not configure a Vercel domain.
Production legal and account-deletion resources must remain publicly reachable
without login or deployment protection. A Git push alone is not a live check.

The `.well-known/assetlinks.json` file includes the local KhelNest certificate
and the owner-supplied Play App Signing SHA-256 certificate (starting `09:64:1E`).
The latter has not been independently checked against a downloaded Play
certificate. Serve this file on the actual website host with HTTP 200 and
application/json; a local file does not establish deployed App Links.
Do not replace the package name or generate a new upload key for routine updates.

## Content Maintenance

Website pages are generated in the app workspace using its shared legal source
and `tool/export_legal_pages.dart`; captured game previews contain no real user
information. Preserve the font license beside the bundled fonts.

Full-resolution game captures remain outside the deployment under
tool/branding/site_previews. The public assets directory uses compact WebP
previews; regenerate them with tool/branding/generate_site_art.py after a capture.

Before a public or closed-test rollout, verify account/auth/provider deletion,
retention durations, support response handling, eligible countries, payout rules,
and current policies. Regenerate the pages after any behavior or wording change.