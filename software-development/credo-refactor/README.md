# Credo Refactor

> 128 issues from `mix credo --strict` after config update, broken into six check
types across four phases.

## Issue Summary

| Check            | Issu

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Credo Refactor Plan

128 issues from `mix credo --strict` after config update, broken into six check
types across four phases.

## Issue Summary

| Check            | Issues | Lib files | Test files |
| ---------------- | -----: | --------: | ---------: |
| MultiAlias       |     49 |        16 |         15 |
| SinglePipe       |     31 |         9 |          7 |
| ImplTrue         |     23 |         3 |          3 |
| PipeChainStart   |     13 |         6 |          3 |
| DuplicatedCode   |      8 |         4 |          2 |
| OnePipePerLine   |      4 |         1 |          2 |

---

## Phase 1 — Mechanical rewrites (MultiAlias, OnePipePerLine)

**53 issues.** Pure syntax changes with no behavioral risk.

### MultiAlias (49 issues, 31 files)

Expand every grouped alias `alias Foo.{Bar, Baz}` into individual lines.

Files (by area):
- **Core lib:** `ltix.ex`, `deployment.ex`, `launch_claims.ex`, `launch_context.ex`,
  `storage_adapter.ex`
- **OIDC:** `oidc/callback.ex`, `oidc/login_initiation.ex`
- **OAuth:** `oauth.ex`, `oauth/client.ex`, `oauth/client_credentials.ex`
- **JWT:** `jwt/token.ex`
- **Services:** `grade_service.ex`, `memberships_service.ex`,
  `memberships_service/member.ex`
- **Test helpers:** `test.ex`, `test/platform.ex`
- **Test files:** 15 files (see Issue Summary)

### OnePipePerLine (4 issues, 3 files)

Break multi-pipe expressions that share a line into separate lines.

- `lib/ltix/memberships_service.ex`
- `test/ltix/jwk_test.exs`
- `test/ltix/jwt/token_test.exs`

**Commit:** `style: expand multi-aliases and fix one-pipe-per-line`

---

## Phase 2 — Pipeline hygiene (SinglePipe, PipeChainStart)

**44 issues.** Overlapping locations — many SinglePipe sites are also
PipeChainStart violations. Fix together per-file to avoid double-touching.

### SinglePipe (31 issues, 16 files)

Replace `value |> fun()` with `fun(value)` when the pipeline is only one
step long.

### PipeChainStart (13 issues, 9 files)

Rewrite pipes that start with a function c

*[truncated — see source for full prompt]*