# Backfill Spec

> ## Status

Draft only. This document records current learnings and a proposed design for a future backfill tool. It does not change the V1 runtime con

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Raider.IO Internal API Backfill Spec

## Status

Draft only. This document records current learnings and a proposed design for a future backfill tool. It does not change the V1 runtime contract in [SPEC.md](../SPEC.md), which remains public-API-first.

## Why This Exists

The current bot intentionally uses Raider.IO's documented public API only. That keeps the main sync path conservative, but it also means historical coverage is incomplete because the public character profile payload only exposes:

- recent runs
- best scoring runs
- alternate scoring runs

That is enough for live summary freshness, but not enough to reliably reconstruct an entire season history after missed polling windows.

We have now identified Raider.IO website endpoints that appear to expose a fuller run history and rich run details. Those endpoints are promising for one-off or occasional backfill, but they are likely internal frontend APIs and should be treated as brittle.

## What We Learned

### Internal endpoints discovered

When expanding a dungeon group on the Raider.IO character page, the site requests:

`/api/characters/mythic-plus-runs`

Observed query shape:

- `season`
- `characterId`
- `dungeonId`
- `role`
- `specId`
- `mode`
- `affixes`
- `date`

Example:

```text
/api/characters/mythic-plus-runs?season=season-mn-1&characterId=1063439&dungeonId=15808&role=all&specId=0&mode=scored&affixes=all&date=all
```

Observed response shape:

- `runs[]`
- `runs[].summary`
- `runs[].summary.keystone_run_id`
- `runs[].summary.logged_run_id`
- `runs[].summary.completed_at`
- `runs[].summary.mythic_level`
- `runs[].summary.clear_time_ms`
- `runs[].summary.keystone_time_ms`
- `runs[].summary.num_chests`
- `runs[].summary.weekly_modifiers`
- `runs[].score`
- `ui`

When opening an individual run from that group, the site requests:

`/api/mythic-plus/runs/{season}/{keystone_run_id}`

Example:

```text
/api/mythic-plus/runs/season-mn-1/66715
```

Observed response shape:

- `keystoneRun`
- `keystone

*[truncated — see source for full prompt]*