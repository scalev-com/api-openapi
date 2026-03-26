# api-openapi

Standalone OpenAPI repository for the Nexus API contract.

## Source of Truth

- Edit `specs/v2/openapi.yaml`
- Do not edit `specs/v2/openapi.json` directly
- `specs/v2/openapi.json` is a generated artifact and is not committed

## Usage

```bash
npm install
npm run lint
npm run build
npm run build:site
```

`npm run build` generates `specs/v2/openapi.json` from the YAML source for local tooling or publishing workflows.
`npm run build:site` creates a publishable `dist/` directory with:

- `dist/index.html` for human-readable API docs
- `dist/specs/v2/openapi.yaml`
- `dist/specs/v2/openapi.json`

When Nexus API behavior changes, update this repo as part of the same work.

## GitHub Pages

The repo includes `.github/workflows/pages.yml`, which:

- validates the YAML spec
- generates JSON from the YAML source
- builds static HTML docs with Redocly
- deploys `dist/` to GitHub Pages from the default branch

After pushing this repo to GitHub:

1. Open repository Settings > Pages.
2. Set Source to `GitHub Actions`.
3. Optionally set a custom domain in the Pages settings.
4. Verify the domain in GitHub and point DNS at GitHub Pages.

With this setup, the published site will expose the docs homepage plus the raw spec files under `/specs/v2/openapi.yaml` and `/specs/v2/openapi.json`.
