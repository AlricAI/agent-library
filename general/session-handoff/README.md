# SESSION HANDOFF

> This is the active handoff surface for new chats.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# LIC Legal Suite Session Handoff

This is the active handoff surface for new chats.

Canonical operations source: `docs/OPERATIONS_PLAYBOOK.md`.
Historical detail: `docs/SESSION_HISTORY_ARCHIVE.md`.

## Snapshot Metadata

- Snapshot File: `tools/backlog-sync/session.snapshot.json`
- Snapshot Timestamp: `2026-03-10T15:14:48.352Z`
- Snapshot Schema Version: `1.1.0`
- Last Successful Mirror Verify: `2026-03-10T15:14:44.847Z`

## Current Operational Status

- Branch baseline: `main`
- Backlog model: Linear canonical, GitHub mirror-only
- Active phase registry: `docs/ACTIVE_PHASES.md`
- Current queued phase: `FRONTEND-REFACTOR` with review branches prepared

Queue conditions:
1. `REQ-EVE2-001`..`REQ-EVE2-011` remain in the matrix, but reconciliation confirmed the previously open EVE-2 slices were already implemented and test-covered.
2. Linear-backed commands are currently healthy in this workspace (`backlog:verify` passing before timestamp drift only).
3. Active frontend-refactor work is isolated to dedicated branches and no longer needs to live as dirty `main` state.

## New Chat Bootstrap

Run:

```bash
pnpm ops:preflight
```

Then follow `docs/OPERATIONS_PLAYBOOK.md`.

## Promotion Protocol (EVE-2)

Use exactly:

```bash
pnpm backlog:seed
pnpm backlog:sync
pnpm backlog:verify
pnpm backlog:matrix:check
pnpm backlog:snapshot
pnpm backlog:handoff:refresh
pnpm backlog:handoff:check
```

Only after this sequence succeeds should EVE-2 issue runs be assigned in Symphony.

## Open Operational Conflicts

1. Frontend refactor review branches are local until pushed/opened (`lin/KAR-119-prd-01-02-foundation`, `lin/KAR-122-prd-05-page-overhaul`).
2. Release smoke runner still has one deterministic failure (`POST /portal/messages` returns 403 when run as admin user); remaining smoke steps pass.

## Short Delta Log

- 2026-02-27: Cleaned local repo clutter by removing patch-equivalent stale branches and stale remote `origin/codex/*` branches; preserved unique/WIP branches and one 

*[truncated — see source for full prompt]*