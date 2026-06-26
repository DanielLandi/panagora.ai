# Legal templates (privacy + terms)

Authoring skeletons for the **privacy policy** and **terms of service** pages
shipped with each Panagora app. Copy these into a new app's marketing-site repo
and fill in the placeholders — they are **not** a runtime dependency, so nothing
links back to this folder.

The reference implementation is **TVCanvas** (`../../../tvcanvas-site/privacy.html`
and `terms.html`) — look there for a fully filled-in example.

## How to use for a new app

1. Copy `privacy.html` and `terms.html` into the new app's site repo root
   (e.g. `myapp-site/privacy.html`, `myapp-site/terms.html`).
2. Replace every `{{PLACEHOLDER}}` (table below).
3. Walk every `<!-- APP-SPECIFIC -->` block: fill it in, or delete the whole
   section if the app doesn't do that thing (Photos access, AI content, IAP…).
   Renumber the Terms sections after deleting any.
4. Leave the `<!-- COMMON -->` sections as-is unless the app genuinely differs.
5. Point App Store Connect at the deployed `…/privacy.html` URL.

## Placeholders

| Token | Meaning | TVCanvas value |
|---|---|---|
| `{{APP_NAME}}` | App display name | `TVCanvas` |
| `{{APP_ONE_LINER}}` | "is …" sentence completion | `an iOS app that generates and transforms art with AI and casts it to your TV` |
| `{{THEME_KEY}}` | localStorage theme key (per-site, must be unique) | `tvcanvas-theme` |
| `{{SUPPORT_EMAIL}}` | Contact address (must be a real mailbox) | `support@tvcanvas.app` |
| `{{LAST_UPDATED}}` | Human date | `April 30, 2026` |
| `{{YEAR}}` | Copyright year | `2026` |
| `{{PROVIDER_NAME}}` / `{{PROVIDER_*}}` | Per-third-party-service fields | OpenAI, Google Gemini, … |
| `{{GOVERNING_STATE}}` / `{{GOVERNING_VENUE}}` | Terms jurisdiction (default) | `Washington` / `King County, Washington` |
| `{{IAP_PRODUCT}}` | Name of the paid offering | `TVCanvas Cloud` |

## The one rule that prevents drift

An app's privacy text often lives in **two runtime places**: the marketing-site
`privacy.html` (App Store canonical) **and** wherever the app shows it in-app
(for TVCanvas, the cloud `GET /legal/privacy` endpoint). These WILL drift if
hand-maintained separately — that's the bug this template set was created after.

**Rule: each app has exactly one canonical privacy document. Every other copy
must be generated from it or kept in lockstep, and reviewed together in the same
change.** Where possible, have the in-app/cloud copy return the site URL rather
than a second hand-edited copy.
