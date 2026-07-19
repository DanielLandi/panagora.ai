# External services

Every external service, API, or paid account this repo depends on.

> **Update rule:** any change that adds, removes, or re-keys an external
> service must update this file in the same commit/PR.

| Service | Purpose |
|---|---|
| **GitHub** | Hosts this public repository. |
| **GitHub Pages** | Hosts the site and public resources at `https://daniellandi.github.io/panagora.ai/`. |
| **Cloudflare** | Domain registration and DNS for `panagora.ai`; managed separately from this repository. |

## Notes

- **Referenced, not depended on:** OpenAI / Google (Gemini) appear only as
  `{{PROVIDER_*}}` placeholder examples in `_templates/legal/` — no keys, no
  API usage in this repo.
- `apps.json` is fetched by shipped TVCanvas iOS apps; its serving URL is a
  de-facto dependency of those apps, not of this repo.
