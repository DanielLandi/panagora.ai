# External services

Public service dependencies for this site.

> **Update rule:** update this file in the same commit whenever a service
> dependency changes. Keep credentials, billing details, and internal
> administration notes out of this public repository.

| Service | Purpose |
|---|---|
| **GitHub** | Hosts this public repository. |
| **GitHub Pages** | Hosts the site and public resources at `https://daniellandi.github.io/panagora.ai/`. |
| **Cloudflare** | Domain registration and DNS for `panagora.ai`; managed separately from this repository. |
| **Cloudflare Email Routing** | Routes email sent to the public privacy contact, `privacy@panagora.ai`. |

## Public resources

- `apps.json` is consumed by TVCanvas apps. Preserve its field shape and
  serving path.
- `integrations/privacy.html` is the public Panagora Integrations privacy
  policy. Preserve its URL for apps and services that link to it.
- Providers named in privacy policies and legal templates describe the
  corresponding apps' data handling; this static site makes no API calls
  to those providers.
