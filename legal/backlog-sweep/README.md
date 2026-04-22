# Backlog Sweep

> Use this contract for any large Linear-Todo, stopped-job, or draft-review sweep where completion depends on exhausting a queue, not just landing code fixes.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Backlog Sweep Contract

Use this contract for any large Linear-Todo, stopped-job, or draft-review sweep where completion depends on exhausting a queue, not just landing code fixes.

## When This Is Required

- Any stopped-job or drafted-job sweep larger than 25 rows
- Any sweep that must exhaust every current Linear `Todo` issue before completion
- Any request with a hard denominator such as "review every draft in the snapshot"
- Any session where `complete` would otherwise depend on a manual queue pass

## Required Files

Every sweep needs immutable snapshots plus append-friendly results ledgers.

## Fast Start

Before any sweep session, resolve the active manifest:

```bash
uv run python scripts/resume_or_start_backlog_sweep.py --active
```

That command resumes the current active sweep when one is valid, or bootstraps a fresh active manifest when none is resumable.
Only replace an existing active sweep intentionally.

If Phase 1 has not been started for the active manifest yet, materialize the Linear Todo snapshot and ledger:

```bash
uv run python scripts/init_backlog_sweep.py --start-phase phase1
```

At the start of Phase 2, materialize the stopped snapshot and ledger:

```bash
uv run python scripts/init_backlog_sweep.py --start-phase phase2
```

At the start of Phase 3, materialize the draft snapshot and ledger:

```bash
uv run python scripts/init_backlog_sweep.py --start-phase phase3
```

That staged flow creates:

- the Phase 1 snapshot
- the Phase 1 results ledger
- the Phase 2 snapshot
- the Phase 2 results ledger
- the Phase 3 snapshot
- the Phase 3 results ledger
- `.context/compound-engineering/todos/current_backlog_sweep.json`

Then the shortest verification command is:

```bash
uv run python scripts/verify_active_sweep.py --active
```

For the checked-in reusable prompt, use [`docs/runbooks/repeatable-backlog-sweep.md`](runbooks/repeatable-backlog-sweep.md).

If you explicitly want to replace the active sweep instead of resuming it, use:

```bash
u

*[truncated — see source for full prompt]*