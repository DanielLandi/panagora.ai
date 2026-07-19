# External services

Every external service, API, or paid account this repo depends on.

> **Update rule:** any change that adds, removes, or re-keys an external
> service must update this file in the same commit/PR.

| Service | What for | Credentials / env | Console / billing notes |
|---|---|---|---|
| **GitHub** | Hosts the repo — **PUBLIC**: anything pushed is world-readable immediately | `gh` CLI auth | Part of the account-wide GitHub paid plan |
| **GitHub Pages** | Serves `main` root at `https://daniellandi.github.io/panagora.ai/` — enabled and built (verified 2026-07-19), but **no custom domain**: the CNAME was deleted (commit `20988cc`), so the `panagora.ai` apex is not wired to this site | none (Pages settings in repo) | Free on public repos |
| **Cloudflare** | `panagora.ai` domain DNS (Cloudflare Registrar). Subdomains are used by `homelab` tunnels and `inner-circle` apps and are **managed in those repos** — only the apex/landing-site concern belongs here, and it currently points nowhere useful for this repo | Cloudflare account (domain-level, owned elsewhere) | `.ai` renewal is premium (~$70–100/yr) |

## Notes

- **Referenced, not depended on:** OpenAI / Google (Gemini) appear only as
  `{{PROVIDER_*}}` placeholder examples in `_templates/legal/` — no keys, no
  API usage in this repo.
- `apps.json` is fetched by shipped TVCanvas iOS apps; its serving URL is a
  de-facto dependency of those apps, not of this repo.
