# Governance

> ## Overview

This document outlines the governance model for the ANTIGRAVITY repository and related projects. These guidelines ensure consistent, secu

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Repository Governance

## Overview

This document outlines the governance model for the ANTIGRAVITY repository and related projects. These guidelines ensure consistent, secure, and mission-aligned development practices across all contributors.

## Branch Policy

This repository follows a **1-branch policy**: `main` is the only long-lived branch.

### Main Branch (Production)

- Protected branch — direct pushes forbidden
- Requires at least 1 approved review from a CODEOWNER
- All four CI status checks must pass before merge:
  - `validate` — build, secret scan, §496.405 scan, doctrine drift
  - `eslint-prettier-check` — TypeScript/React style
  - `black-ruff-check` — Python style
  - `run-tests` — backend tests (≥80% coverage)
- Branches must be up-to-date with `main` before merge
- Auto-delete head branch enabled
- No long-lived side branches (`develop`, `staging`, `release/*`, etc.)

### Short-lived Feature and Fix Branches

- Naming: `feat/`, `fix/`, `chore/`, `docs/`, `claude/`, `codex/` prefixes
- Created from `main`, merged to `main`, deleted immediately after merge
- See `CONTRIBUTING.md` for the full PR workflow

## Pull Request Approval Rules

### Review Requirements

- All PRs require at least 1 review from a CODEOWNER
- High-risk changes require 2 reviews
- CODEOWNERS are defined in the `.github/CODEOWNERS` file

### Approval Criteria

- Code follows established style guides
- Adequate test coverage (minimum 80%)
- No new linting errors
- Security considerations addressed
- Breaking changes documented
- Changelog updated

### Merge Requirements

- All CI status checks must pass
- No "Changes requested" reviews outstanding
- PR description must be filled out
- Self-approval prohibited

## Release and Versioning

### Versioning Scheme

We follow Semantic Versioning 2.0.0:

- MAJOR version for incompatible API changes
- MINOR version for backward-compatible functionality
- PATCH version for backward-compatible bug fixes

### Release Process

1. All work me

*[truncated — see source for full prompt]*