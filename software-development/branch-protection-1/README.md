# BRANCH PROTECTION

> **Date:** April 3, 2026
**Standard:** revvel-standards/CONCURRENT_DEVELOPMENT_STANDARD.md
**Status:** Mandatory Policy

---

## 1. Overview

Branch pr

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Branch Protection Rules — Reese Reviews

**Date:** April 3, 2026
**Standard:** revvel-standards/CONCURRENT_DEVELOPMENT_STANDARD.md
**Status:** Mandatory Policy

---

## 1. Overview

Branch protection rules are enforced on the `main` branch of the `reese-reviews` repository to prevent accidental overwrites, ensure code quality, and maintain a stable production deployment. These rules align with the Revvel Concurrent Development Standard and the No Force Push Policy established after the MindMappr incident on April 3, 2026.

---

## 2. Protected Branch: `main`

The following rules are configured (or must be configured) on the `main` branch via GitHub Settings or the GitHub API.

| Rule | Setting | Rationale |
| :--- | :--- | :--- |
| **Require pull request before merging** | Enabled | All changes must go through a PR for review. |
| **Required approving reviews** | 1 minimum | At least one reviewer (human or CodeRabbit) must approve. |
| **Dismiss stale PR reviews** | Enabled | New pushes to a PR branch invalidate previous approvals. |
| **Require status checks to pass** | Enabled | CI pipeline (lint, typecheck, build, test) must pass. |
| **Required status checks** | `ESLint`, `TypeScript Type Check`, `Vitest Unit & Integration Tests`, `Vite Production Build` | All four CI jobs must succeed. |
| **Require branches to be up to date** | Enabled | PR branch must be rebased on latest `main`. |
| **Require linear history** | Recommended | Prefer rebase over merge commits for clean history. |
| **Allow force pushes** | **Disabled** | Force-push is permanently banned per CODE_REVIEW_STANDARD. |
| **Allow deletions** | Disabled | The `main` branch cannot be deleted. |
| **Restrict who can push** | Repository admins only | Direct pushes to `main` are blocked for all other contributors. |

---

## 3. How to Apply via GitHub API

The following script applies branch protection rules programmatically. Replace `YOUR_PAT` with a GitHub Personal Access Token that has `repo` scope.

*[truncated — see source for full prompt]*