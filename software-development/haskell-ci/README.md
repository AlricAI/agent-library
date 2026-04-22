# Haskell Ci

> ## Overview

The Haskell CI workflow builds, tests, and packages the Haskell automation codebase on every push that touches Haskell source files or th

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Haskell CI

## Overview

The Haskell CI workflow builds, tests, and packages the Haskell automation codebase on every push that touches Haskell source files or the workflow definition itself.

## Trigger

- Push to any branch, or pull request, when files match the path filter
- Path filter: `haskell/**` and `.github/workflows/haskell.yml`
- The `pull_request` trigger ensures Haskell CI appears as a check on PRs that touch Haskell files, even when the latest commit in the PR only changes non-Haskell files
- Concurrency: one run per branch, cancels in-progress runs on new pushes

## Build Environment

- Runs on `ubuntu-latest` inside the `haskell:9.14.1` container (GHC 9.14.1 + Cabal)
- Permissions: `contents: read` only
- `CABAL_DIR` is set to `/github/home/.cabal` to force cabal to use the old-style directory layout, ensuring cache paths match where cabal actually reads and writes packages. Without this, modern cabal (3.10+) defaults to XDG Base Directory paths (e.g. `~/.local/state/cabal/store`), which would not match the `~/.cabal/store` cache path.

## Jobs

The workflow runs two parallel jobs for maximum throughput:

### build-and-test

Builds the project, runs tests, and produces artifacts.

### lint

Runs HLint independently and in parallel with the build.

## Caching Strategy

Three directories are cached for fast incremental builds:

1. `~/.cabal/store` — pre-built dependency packages
2. `~/.cabal/packages` — downloaded Hackage package tarballs and index
3. `haskell/dist-newstyle` — project compilation artifacts (object files, interface files, executables)

Cache key structure (three-tier fallback):

- **Exact key:** hash of `automation.cabal` + `cabal.project` + hash of all source files (`src/**`, `app/**`, `test/**`)
- **First fallback:** hash of `automation.cabal` + `cabal.project` only (dependencies match, project incrementally recompiled)
- **Second fallback:** any previous `cabal-ghc914v2-` key (best-effort partial cache)

## Update Hackage Index Ste

*[truncated — see source for full prompt]*