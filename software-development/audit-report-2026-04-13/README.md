# AUDIT REPORT 2026 04 13

> **Date:** 2026-04-13
**Scope:** Full codebase — Go backend (hypergoat), Next.js admin client, Docker/CI, dependencies
**Methodology:** Multi-pass AI-a

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Security & Code Quality Audit Report

**Date:** 2026-04-13
**Scope:** Full codebase — Go backend (hypergoat), Next.js admin client, Docker/CI, dependencies
**Methodology:** Multi-pass AI-assisted audit (10 specialist reviewers, adversarial cross-review, 3 full passes)
**Auditor:** Claude Opus 4.6 (AI agent)

---

## Executive Summary

**Security posture:** The codebase has a solid security foundation — parameterized SQL queries, constant-time secret comparisons, CORS enforcement, depth-limited GraphQL, body size caps, and non-root Docker containers. However, several Critical-severity issues existed: a hardcoded cookie secret default that could allow session forgery, hardcoded production infrastructure URLs in public-facing code, and a non-existent Go version in the build system. These have been fixed in this audit.

**Code quality:** Well-structured Go code with clear separation of concerns. The 23-round review history (PR #25) already addressed many common issues. Main debt: a few swallowed errors in the OAuth layer, missing security linters, and the client lacks defense-in-depth (relies entirely on backend authorization).

**Top 3 items to address before next ship:** (1) Upgrade `golang.org/x/crypto` to >= v0.31.0 (CVE-2024-45337), (2) implement label signature verification in the labeler consumer, (3) verify production `SECRET_KEY_BASE` and `COOKIE_SECRET` are unique per environment.

---

## Findings Summary

| Severity | Count | Fixed | Remaining |
|----------|-------|-------|-----------|
| Critical | 4 | 4 | 0 |
| High | 5 | 5 | 0 |
| Medium | 8 | 6 | 2 |
| Low | 7 | 0 | 7 |
| Info | 5 | 0 | 5 |
| **Total** | **29** | **15** | **14** |

---

## Critical Findings (All Fixed)

### F-BUILD-001: Non-existent Go version (go 1.25) — FIXED in CS-001
- **Location:** `go.mod:3`, `Dockerfile:2`
- **Impact:** Build behavior unpredictable; GOTOOLCHAIN=auto could download arbitrary toolchain
- **Fix:** Pinned to go 1.23, alpine:3.21, GOTOOLCHAIN=local

### F-CLIENT-COOKI

*[truncated — see source for full prompt]*