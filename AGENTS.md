# panagora.ai

Static Panagora landing page (`index.html`), the **canonical `apps.json`
cross-promo catalog** consumed by the TVCanvas app suite, and the
**legal-page templates** (`_templates/legal/`) that new Panagora apps copy
for their privacy/terms pages. No build step, no runtime code.

> **Repo is PUBLIC.** Anything pushed here is world-readable immediately —
> no secrets, no internal notes, no unreleased app names.

## Contribution flow

This is a **Tier C repo** (static site / config): edit and push to `main`
directly. A push triggers a GitHub Pages rebuild.

**Hosting status (verified 2026-07-19):** GitHub Pages is enabled and built,
serving `main` root at `https://daniellandi.github.io/panagora.ai/`. It is
**not wired to the `panagora.ai` apex** — the CNAME file was deleted (commit
`20988cc`), so the custom domain is disconnected. Apps fetch `apps.json` by
whatever URL they were shipped with; confirm the consumer URL before moving
or renaming anything.

## Work tracking

GitHub Issues is the single source of truth for pending work — no file-based
trackers. Capture follow-ups with the `inbox` skill; milestones are umbrella
issues (`gh issue list --label milestone`); close via PR with `Closes #n` (or
reference the issue from the commit). For sandboxed sessions pass
`-R DanielLandi/panagora.ai` to `gh`.

## Data contracts

These public resources are contracts with other repos/apps — change them carefully:

- **`apps.json`** — the canonical cross-promo app catalog (currently the four
  TVCanvas apps, bundle ids `com.daniellandi.tvcanvas*`). Consumed by the
  shipped iOS apps' "More apps" surfaces. Additive changes only unless every
  consumer is updated; keep `version` and the field shape
  (`id`/`bundleId`/`title`/`subtitle`/`icon`/`appStoreURL`) stable.
- **`_templates/legal/`** — authoring skeletons for each app's privacy policy
  and terms pages. They are copied into per-app site repos and
  `{{PLACEHOLDER}}`-filled — **not** a runtime dependency; nothing links back
  here. See [`_templates/legal/README.md`](./_templates/legal/README.md) for
  the placeholder table, the TVCanvas reference implementation
  (`tvcanvas-site/`), and the one anti-drift rule (each app has exactly one
  canonical privacy document).

- **`integrations/privacy.html`** — public privacy policy for Panagora
  Integrations. Keep this path stable for apps and services that link to it.
  It covers authorized integration tests, not every Panagora app. Other apps
  should publish their own accurate policy using the legal templates above.

## Domain note

Domain administration is managed separately from this repository. Only the
landing site and public resources maintained here are in scope; do not change
unrelated DNS records or services as part of site updates.

## External services

See [`SERVICES.md`](./SERVICES.md) — update it in the same commit whenever a
service dependency changes.
