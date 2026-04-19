# ScreenJSON Documentation

Source for [docs.screenjson.com](https://docs.screenjson.com).

Built with [Mintlify](https://mintlify.com). Pushes to `main` auto-deploy.

## Structure

```
docs.json                          Mintlify site config
index.mdx                          Tab: Guides → Introduction
quickstart.mdx                     Tab: Guides → Quickstart
install.mdx                        Tab: Guides → Install
concepts/                          Tab: Guides → Core concepts
tools/
  export/                          Tab: Tools → screenjson-export
  cli/                             Tab: Tools → screenjson-cli
  ui/                              Tab: Tools → screenjson-ui
  greenlight/                      Tab: Tools → Greenlight
specification/                     Tab: Specification (schema reference)
api-reference/
  cli/openapi.json                 OpenAPI for screenjson serve
  cli/introduction.mdx             Tab: API Reference → screenjson-cli server
  greenlight/openapi.json          OpenAPI for Greenlight
  greenlight/introduction.mdx      Tab: API Reference → Greenlight service
logo/                              Logo SVGs (light + dark)
favicon.svg                        Favicon
```

Mintlify auto-generates endpoint pages under the `endpoint/` subdirectories from each `openapi.json`.

## Local development

```bash
npm install -g mintlify
mintlify dev
```

Runs a preview at `http://localhost:3000` with hot reload.

## Adding a page

1. Create an `.mdx` file under the appropriate directory.
2. Add its path to the matching `pages:` array in `docs.json`.
3. Commit and push — Mintlify deploys on merge to `main`.

## Updating the OpenAPI specs

- `api-reference/cli/openapi.json` — update when `screenjson serve` endpoints change. Source of truth is [`screenjson-cli/internal/server/server.go`](https://github.com/screenjson/screenjson-cli).
- `api-reference/greenlight/openapi.json` — mirrored from [`greenlight/openapi.json`](https://github.com/screenjson/greenlight).

Mintlify regenerates the per-endpoint pages automatically on deploy.
