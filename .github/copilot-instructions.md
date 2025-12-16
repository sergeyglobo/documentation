# Copilot instructions for Vimapay docs

Purpose: Help AI coding agents be immediately productive editing the Mintlify-based documentation site.

Key context
- **Site engine:** Mintlify (Mint) static docs driven by `docs.json` and `.mdx` pages.
- **Dev scripts:** see `package.json` — use `npm run dev` (runs `npx mintlify dev --port 3333`) and `npm run install:mintlify` to (re)install Mintlify.
- **Node requirement:** Node >= 18 as declared in `package.json`.

Big-picture architecture (what matters)
- `docs.json` is the central site config and navigation. It declares `products`, `tabs`, `groups`, `pages`, and `openapi` references. Edit this file to change navigation or add pages.
- Content lives as MDX files grouped by purpose: see `products/`, `api-reference/`, `endpoint/`, `integration/`, `essentials/`, `snippets/`.
- API reference is driven by `api-reference/openapi.json` — updating this file affects the generated API pages under the "API-методы" group in `docs.json`.
- Static assets (images, logo) live in `images/` and `logo/` and are referenced from `docs.json` and MDX pages.

Project-specific conventions and examples
- Navigation entries reference pages without file extensions. Example: `products/card` corresponds to `products/card.mdx`.
- API integration pages are under `api-reference/integration/` and `endpoint/` contains individual endpoint docs (e.g., `endpoint/checkout.mdx`).
- To add a new doc:
  - create `X.mdx` under an appropriate folder (e.g., `products/`),
  - add `"products/X"` to the relevant `pages` array in `docs.json`,
  - run `npm run dev` and verify the new page appears.
- Keep `docs.json` valid JSON. The Mintlify CLI reads it strictly — malformed JSON will break the local dev server.

Development & debugging workflow (concrete)
- Start local preview: `npm install` (if needed) then `npm run dev`.
- Reinstall Mintlify CLI wrapper: `npm run install:mintlify`.
- Server watches `.mdx` and `docs.json`; reload occurs automatically.
- If a page returns 404, confirm the `pages` path in `docs.json` matches the MDX file location and name.

Integration points & external dependencies
- Mintlify CLI (`npx mintlify`) — used for dev preview & tooling.
- `api-reference/openapi.json` — single source for API schema used by the docs generator.
- Deployment is managed via a GitHub App (see `README.md`); pushes to default branch trigger deploys.

Useful files to inspect
- [docs.json](docs.json) — site config and navigation
- [package.json](package.json) — scripts and Node engine
- [README.md](README.md) — project overview and dev tips
- [api-reference/openapi.json](api-reference/openapi.json) — OpenAPI spec powering API pages
- `products/`, `endpoint/`, `integration/`, `essentials/`, `snippets/` — content folders

Agent behaviour guidance (do this here)
- Prefer editing an existing MDX file over creating a new, similarly-named duplicate.
- When changing navigation in `docs.json`, validate JSON and then run `npm run dev` to confirm.
- When updating API docs, update `api-reference/openapi.json` and check the relevant `docs.json` group referencing `openapi`.
- Preserve Russian content and existing wording unless asked to translate — the site primarily contains RU texts.

If anything is unclear or you want the instructions expanded (examples, checklist, or automated tests), tell me which section to expand.
