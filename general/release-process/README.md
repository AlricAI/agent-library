# RELEASE PROCESS

> This document describes the automated release process for floop using GoReleaser.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Release Process

This document describes the automated release process for floop using GoReleaser.

## Overview

The release pipeline is fully automated with semantic version bumping:
1. Code merges to `main` trigger automatic version detection from commit messages
2. Commits are parsed for conventional commit prefixes: `feat:` → minor, `fix:`/`perf:` → patch, breaking changes → major
3. Chore-only merges (docs, ci, test, refactor, etc.) skip the release entirely
4. GoReleaser builds binaries, publishes to GitHub Releases, and updates the Homebrew tap

## Installation

### Homebrew (macOS/Linux)

```bash
brew install nvandessel/tap/floop
```

### Go

```bash
go install github.com/nvandessel/floop/cmd/floop@latest
```

### Manual

Download binaries from [GitHub Releases](https://github.com/nvandessel/floop/releases), extract, and add to your PATH.

## Auto-Release

Every push to `main` that changes code files triggers `auto-release.yml`. Documentation-only changes (`.md`, `docs/`, `.beads/`, `.floop/`, `LICENSE`) and workflow changes (`.github/`) are ignored via `paths-ignore`. CI (Test, Lint, Build) is enforced as a required status check via GitHub rulesets, so it must pass before merge.

### Semantic Version Bumping

Since the repo uses squash-merge, PR titles become commit messages. The `pr-title.yml` workflow enforces conventional commit format on PR titles. Version bumping uses [`svu`](https://github.com/caarlos0/svu) (by the GoReleaser maintainer) to parse commits since the last tag and determine the bump type:

| Commit Type | Bump | Example |
|-------------|------|---------|
| `feat!:` or `BREAKING CHANGE:` in body | **major** | `feat!: remove legacy API` |
| `feat:` | **minor** | `feat: add --tags flag` |
| `fix:`, `perf:` | **patch** | `fix: handle empty input` |
| `chore:`, `ci:`, `test:`, `docs:`, `build:`, `style:`, `refactor:` | **skip** | `chore: update deps` |

### Skip Mechanisms

| Method | Use Case |
|--------|----------|
| `github-actions[bot]` 

*[truncated — see source for full prompt]*