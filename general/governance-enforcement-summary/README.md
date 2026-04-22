# GOVERNANCE ENFORCEMENT SUMMARY

> **TL;DR**: Turn AGENTS.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Governance Enforcement: Quick Wins Summary

**TL;DR**: Turn AGENTS.md rules into automated contracts via pre-commit hooks and linting. Four rules, phased rollout, 8–12 hours total effort for maximum impact.

---

## The Problem

AGENTS.md defines critical governance rules (error handling, RLS coverage, documentation updates), but they're guidelines—not enforced. This leads to:
- Silent authorization failures (missing RLS)
- Stale documentation causing operational confusion
- Error-only toast messages that fade away
- Inconsistent commit messages

---

## The Solution: Four Quick-Win Rules

| Rule | Mechanism | Effort | Impact | Phase |
|------|-----------|--------|--------|-------|
| **Conventional Commits** | commitlint (pre-commit) | 30 min | High (clarity, changelog automation) | 1 |
| **RLS Coverage** | Shell script scan (pre-commit) | 2-3 hrs | Critical (security) | 2 |
| **Docs Sync** | Node.js script (pre-commit) | 2-3 hrs | High (prevents stale docs) | 3 |
| **Error Handling** | ESLint rule | 3-5 hrs | Medium (UX) | 4 (optional) |

---

## Rule Details

### 1. Conventional Commits (Phase 1)
**What**: Enforce commit message format (`feat(scope): description`)  
**Why**: Clear intent, automated changelog, semantic versioning  
**Tool**: @commitlint/cli + husky  
**Blocker**: Yes (commit fails if format is wrong)  
**Reversible**: Yes (remove `.husky/commit-msg`)

```bash
✓ feat(ui): add error validation
✓ fix(api): prevent duplicate logs
✗ oops (no type/scope)
```

---

### 2. RLS Coverage Scanning (Phase 2)
**What**: Ensure all user-scoped tables have RLS policies  
**Why**: Prevents silent authorization bypass  
**Tool**: Custom Node.js script scanning migrations  
**Blocker**: No (warning initially, blocker after audit)  
**Reversible**: Yes (remove from pre-commit)

```bash
✓ blogs: 4 policies
✓ profiles: 3 policies
✗ app_settings: 0 policies
  (intentional for global settings)
```

---

### 3. Documentation Sync Check (Phase 3)
**What**: Code changes mu

*[truncated — see source for full prompt]*