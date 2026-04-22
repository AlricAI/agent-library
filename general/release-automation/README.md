# Release Automation

> This repository uses tag-driven publish workflows.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Generic Release Automation

This repository uses tag-driven publish workflows. The script below standardizes:

- canonical tag creation for each release target
- release note generation from previous release to current commit
- GitHub Release create/update

Script path:

- `scripts/release/create-release.sh`

## Supported Targets

- `js/sandbox`
- `js/code-interpreter`
- `python/sandbox`
- `python/code-interpreter`
- `python/mcp/sandbox`
- `java/sandbox`
- `java/code-interpreter`
- `csharp/sandbox`
- `csharp/code-interpreter`
- `cli`
- `server`
- `docker/execd`
- `docker/code-interpreter`
- `docker/ingress`
- `docker/egress`
- `k8s/controller`
- `k8s/task-executor`
- `helm/opensandbox`
- `helm` (alias of `helm/opensandbox`)

## Tag Rules

The script aligns with existing workflow triggers:

- v-prefixed tags:
  - `<target>/v<version>` for SDK/CLI/Server targets
  - examples: `js/sandbox/v1.0.5`, `server/v0.2.0`
- plain suffix tags:
  - `<target>/<version>` for docker/k8s/helm targets
  - examples: `docker/execd/v0.3.0`, `helm/opensandbox/0.1.0`

## Release Notes Format

Generated notes follow `docs/RELEASE_NOTE_TEMPLATE.md` sections:

- `## What's New`
- `### ✨ Features`
- `### 🐛 Bug Fixes`
- `### ⚠️ Breaking Changes`
- `### 📦 Misc`
- `## 👥 Contributors`

Commit categorization:

- `feat:` -> Features
- `fix:` -> Bug Fixes
- `BREAKING CHANGE` or `type!:` -> Breaking Changes
- everything else -> Misc

## Usage

```bash
scripts/release/create-release.sh --target <target> --version <version> [options]
```

Required:

- `--target`
- `--version`

Options:

- `--from-tag <tag>`: explicit previous release boundary
- `--path <path>`: append custom path filter (repeatable)
- `--no-path-filter`: disable default target path scope and use whole range
- `--initial-release`: allow no previous tag; use full history
- `--dry-run`: render computed tag/range/notes without side effects
- `--push`: push created tag to origin

## Path Filtering Strategy

By default, each target only 

*[truncated — see source for full prompt]*