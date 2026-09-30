# Dealeasy API docs

Public developer documentation for the Dealeasy API, built with [Mintlify](https://mintlify.com).

## Local preview

```bash
npm install
npx mint dev          # http://localhost:3000
npx mint broken-links
npx mint validate
```

## Structure

- `docs.json` - site config and navigation
- `openapi.yaml` - API spec (drives the API reference page and playground)
- `*.mdx` - pages

Pushes to the default branch deploy automatically once the repo is connected in the Mintlify dashboard.
