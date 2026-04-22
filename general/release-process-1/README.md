# RELEASE PROCESS

> This document outlines the steps to create and publish a new release of Tandem.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Release Process

This document outlines the steps to create and publish a new release of Tandem.

> [!IMPORTANT]
> Binary/app release and registry publishing are intentionally separated:
>
> - `.github/workflows/release.yml` handles desktop binaries + GitHub Release assets.
> - `.github/workflows/publish-registries.yml` handles crates.io and npm publishing.

## Overview

Tandem uses **Git tags** to trigger automated builds and releases. When you push a tag matching the pattern `v*.*.*` (e.g., `v0.1.10`), GitHub Actions automatically:

- Builds the application for all platforms (Windows, macOS, Linux)
- Creates a GitHub Release with the built artifacts
- Publishes the release notes

## Registry Publish Workflow (Crates + npm)

Use the separate workflow `.github/workflows/publish-registries.yml` to publish registries.

### Triggers

- Manual: **Actions -> Publish Registries -> Run workflow**
- Tag-based: push a dedicated tag `publish-v<version>` (for example `publish-v0.3.3`)

### Manual workflow inputs

When running `publish-registries.yml` manually, set:

- `version`
- `publish_crates` (boolean)
- `publish_npm` (boolean)
- `publish_pypi` (boolean, independent toggle for Python package release)
- `dry_run` (boolean)

Notes:

- `publish_pypi` is intentionally decoupled from npm so Python release can be skipped/enabled independently.
- Tag-triggered `publish-v<version>` runs still enable crates/npm/PyPI together by default.

### Guardrails

- Uses protected environment `registry-publish` for approval-gated publish jobs.
- Requires crates secret:
  - `CARGO_REGISTRY_TOKEN`
- npm publishing uses **Trusted Publishing (OIDC)** in GitHub Actions by default (no `NPM_TOKEN` required in CI).
- npm publish job enforces tokenless npm config (`NPM_CONFIG_USERCONFIG`) so Trusted Publishing is used instead of stale token auth.
- Token auth is only used when `NPM_PUBLISH_FORCE_TOKEN=true` is set in GitHub Actions variables and `NPM_TOKEN` is present. This is an escape hatch for pa

*[truncated — see source for full prompt]*