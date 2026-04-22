# PUBLISHING

> Low-level reference for how Paperclip packages are prepared and published to npm.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Publishing to npm

Low-level reference for how Paperclip packages are prepared and published to npm.

For the maintainer workflow, use [doc/RELEASING.md](RELEASING.md). This document focuses on packaging internals.

## Current Release Entry Points

Use these scripts:

- [`scripts/release.sh`](../scripts/release.sh) for canary and stable publish flows
- [`scripts/create-github-release.sh`](../scripts/create-github-release.sh) after pushing a stable tag
- [`scripts/rollback-latest.sh`](../scripts/rollback-latest.sh) to repoint `latest`
- [`scripts/build-npm.sh`](../scripts/build-npm.sh) for the CLI packaging build

Paperclip no longer uses release branches or Changesets for publishing.

## Why the CLI needs special packaging

The CLI package, `paperclipai`, imports code from workspace packages such as:

- `@paperclipai/server`
- `@paperclipai/db`
- `@paperclipai/shared`
- adapter packages under `packages/adapters/`

Those workspace references are valid in development but not in a publishable npm package. The release flow rewrites versions temporarily, then builds a publishable CLI bundle.

## `build-npm.sh`

Run:

```bash
./scripts/build-npm.sh
```

This script:

1. runs the forbidden token check unless `--skip-checks` is supplied
2. runs `pnpm -r typecheck`
3. bundles the CLI entrypoint with esbuild into `cli/dist/index.js`
4. verifies the bundled entrypoint with `node --check`
5. rewrites `cli/package.json` into a publishable npm manifest and stores the dev copy as `cli/package.dev.json`
6. copies the repo `README.md` into `cli/README.md` for npm metadata

After the release script exits, the dev manifest and temporary files are restored automatically.

## Package discovery and versioning

Public packages are discovered from:

- `packages/`
- `server/`
- `ui/`
- `cli/`

The version rewrite step now uses [`scripts/release-package-map.mjs`](../scripts/release-package-map.mjs), which:

- finds all public packages
- sorts them topologically by internal dependencies
- r

*[truncated — see source for full prompt]*