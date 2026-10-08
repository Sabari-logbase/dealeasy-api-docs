# Dealeasy API docs

Public developer documentation for the Dealeasy API, built with [Mintlify](https://mintlify.com). It covers integrations, authentication, the campaigns endpoints, error codes, and the headless and custom-app guides.

## Requirements

- Node.js 18 or later
- npm

## Setup

```bash
npm install
```

## Commands

| Command | What it does |
| --- | --- |
| `npm run dev` | Starts a local preview at http://localhost:3000, with live reload on save |
| `npm run dev -- --port 3333` | Starts the preview on another port |
| `npm run validate` | Checks the build in strict mode: `docs.json`, `openapi.yaml` and all pages. Fails on warnings |
| `npm run links` | Checks every internal link for broken targets |
| `npm run a11y` | Checks pages for accessibility issues |
| `npm run check` | Runs `validate` and then `links`. Run it before every push |
| `npm test` | Same as `npm run check` |

The first run of any command can take a minute while Mintlify downloads its local preview client.

## Testing locally

1. Run `npm run dev` and open http://localhost:3000.
2. Click through every page in the sidebar. Edits to `.mdx`, `docs.json` and `openapi.yaml` reload automatically.
3. On **Get specific product campaigns** and **List product campaigns**, use **Try it** to check the playground. Without a live API host, the request will fail; that's expected. Check the form fields, headers and examples instead.
4. Stop the server with `Ctrl+C`, then run `npm run check`.

## Structure

```
docs.json                       site config and sidebar navigation
openapi.yaml                    API spec; drives the endpoint pages and playground
index.mdx                       Overview
getting-started/                Create an integration, Authentication
campaigns/                      Campaigns overview, endpoint pages, campaign object
errors/error-codes.mdx          Error reference
guides/                         Shopify headless, Shopify custom app
favicon.svg
```

- To add a page, create the `.mdx` file and add its path, without the extension, to `navigation` in `docs.json`.
- Endpoint pages use `openapi: "METHOD /path"` frontmatter, so their parameters, schemas and examples come from `openapi.yaml`. Change the spec, not the page, when the API changes.

## Before publishing

- Replace the placeholder base URL `https://api.dealeasy.app` in `openapi.yaml` and the `.mdx` examples with the production host.
- Run `npm run check`.

## Deploying

The repo is connected to the Mintlify dashboard. Every push to `main` deploys automatically:

```bash
npm run check
git add -A
git commit -m "Describe the change"
git push origin main
```
