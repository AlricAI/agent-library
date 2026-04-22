# RELEASE AUTOMATION SETUP

> This document covers the GitHub and npm setup required for the current Paperclip release model:

- automatic canaries from `master`
- manual stable pr

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Release Automation Setup

This document covers the GitHub and npm setup required for the current Paperclip release model:

- automatic canaries from `master`
- manual stable promotion from a chosen source ref
- npm trusted publishing via GitHub OIDC
- protected release infrastructure in a public repository

Repo-side files that depend on this setup:

- `.github/workflows/release.yml`
- `.github/CODEOWNERS`

Note:

- the release workflows intentionally use `pnpm install --no-frozen-lockfile`
- this matches the repo's current policy where `pnpm-lock.yaml` is refreshed by GitHub automation after manifest changes land on `master`
- the publish jobs then restore `pnpm-lock.yaml` before running `scripts/release.sh`, so the release script still sees a clean worktree

## 1. Merge the Repo Changes First

Before touching GitHub or npm settings, merge the release automation code so the referenced workflow filenames already exist on the default branch.

Required files:

- `.github/workflows/release.yml`
- `.github/CODEOWNERS`

## 2. Configure npm Trusted Publishing

Do this for every public package that Paperclip publishes.

At minimum that includes:

- `paperclipai`
- `@paperclipai/server`
- `@paperclipai/ui`
- public packages under `packages/`

### 2.1. In npm, open each package settings page

For each package:

1. open npm as an owner of the package
2. go to the package settings / publishing access area
3. add a trusted publisher for the GitHub repository `paperclipai/paperclip`

### 2.2. Add one trusted publisher entry per package

npm currently allows one trusted publisher configuration per package.

Configure:

- workflow: `.github/workflows/release.yml`

Repository:

- `paperclipai/paperclip`

Environment name:

- leave the npm trusted-publisher environment field blank

Why:

- the single `release.yml` workflow handles both canary and stable publishing
- GitHub environments `npm-canary` and `npm-stable` still enforce different approval rules on the GitHub side

### 2.3

*[truncated — see source for full prompt]*