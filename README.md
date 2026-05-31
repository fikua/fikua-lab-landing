# Fikua Lab — Landing page

Landing page for the Fikua Lab, the OpenID Foundation conformance and
EUDI ARF playground. Served at **<https://lab.fikua.com>**.

## What lives here

```text
.
├── index.html      Landing page
├── style.css       Page styles
├── app.js          Theme toggle
├── favicon.svg
└── shared/         Vendored assets shared across all *.lab.fikua.com frontends
    ├── favicon.svg
    ├── 404.html
    └── 50x.html
```

The site is **fully static** — no build step. Cloudflare Workers serves
the directory as-is.

## Hosting

- **Production:** Cloudflare Workers Static Assets (project
  `fikua-lab-landing`), custom domain `lab.fikua.com`.
- **DNS:** managed via OpenTofu in
  [`fikua-platform-iac/tofu/cloudflare/`](https://github.com/fikua/fikua-platform-iac).
- **Local preview:** open `index.html` directly, or
  `npx wrangler dev` once you `npm i -g wrangler`.

## Releases

Every push to `main` is deployed automatically by the Workers project's
GitHub integration; pull requests get a preview URL.

## Architecture decisions

- ADR 0008 — Fikua Lab frontends on Cloudflare Workers
  (`fikua-platform-iac/docs/adrs/0008-fikua-lab-frontends-on-cloudflare-workers.md`)
- Why subdomain-per-component (and not paths): OID4VC issuer URLs are
  hard-coded into `.well-known/openid-credential-issuer` and into
  every credential offer already in the wild.

## License

Apache-2.0. See [LICENSE](LICENSE).
