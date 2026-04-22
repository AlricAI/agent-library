# Brain Monitor Error Checking Rules

> description: Brain monitor validation workflow and error management globs: - "_errors/**/*"

## Tags
`typescript`

## System Prompt
---
description: Brain monitor validation workflow and error management
globs:
  - "_errors/**/*"
  - "_logs/**/*"
scopes:
  - validation
  - monitoring
  - testing
alwaysApply: false
---

# Brain Monitor Error Checking Rules

## 🧠 MANDATORY: Check Brain Monitor Reports First

Before running ANY validation commands, ALWAYS check the brain-monitor reports:

```bash
# 1. Check overall validation status FIRST
cat _errors/validation-summary.md

# 2. Check specific error reports if needed
cat _errors/reports/errors.typecheck-failures.md
cat _errors/reports/errors.test-failures-*.md
cat _errors/reports/errors.lint-failures.md
cat _errors/reports/errors.format-failures.md
```

## 📁 Brain Monitor Directory Structure

```txt
_errors/
├── validation-summary.md      # Overall status - check this FIRST
├── reports/                   # Detailed error reports
│   ├── errors.typecheck-failures.md
│   ├── errors.lint-failures.md
│   ├── errors.format-failures.md
│   └── errors.test-failures-*.md
└── .counts/                   # Hidden run count tracking

_logs/                         # Real-time server logs
└── [app-name].log
```

## 🚀 Brain Monitor Commands

| Task | Command | Output Location |
|------|---------|-----------------|
| All Validations | `pnpm brain:validate` | `_errors/validation-summary.md` |
| Watch Mode (Fast) | `pnpm brain:watch` | `_errors/watch-summary.md` + individual reports |
| Watch Mode (All) | `pnpm brain:watch --all` | `_errors/watch-summary.md` + individual reports |
| TypeScript Only | `pnpm brain:typecheck-failures` | `_errors/reports/errors.typecheck-failures.md` |
| Lint Only | `pnpm brain:lint-failures` | `_errors/reports/errors.lint-failures.md` |
| Format Only | `pnpm brain:format-failures` | `_errors/reports/errors.format-failures.md` |
| Unit Tests | `pnpm brain:test-failures-unit` | `_errors/reports/errors.test-failures-unit.md` |
| Integration Tests | `pnpm brain:test-failures-integration` | `_errors/reports/errors.test-failures-integrati

*[truncated — see source for full prompt]*