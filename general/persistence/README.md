# Persistence

> Outlines snapshot and event-log mechanisms for durability and fast restarts.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Persistence and Recovery (Optional)

Outlines snapshot and event-log mechanisms for durability and fast restarts.

## Snapshot

- Contents: WM (facts), Alpha memories, Beta memories (tokens), Agenda state, Refraction table, Network version.
- Format: Erlang term external format (`:erlang.term_to_binary/1`) with versioned envelope.
- Consistency: Captured at batch boundaries; agenda paused during snapshot.
- Partitioned: Capture snapshots per partition concurrently to limit pause time and memory spikes. Merge manifests into a tenant-level snapshot set.
- Ruleset Pinning: Record `{ruleset_id, version}` in snapshot header to preserve deterministic replay.

## Restore

- Verify network version compatibility; attempt migration if minor.
- Load snapshot; rebuild indexes; resume agenda.
- Parallel Restore: Load partitions in parallel; defer agenda until all partitions are online.
- Ruleset Activation: Ensure referenced compiled ruleset is present; load if missing before resuming agenda.
- Cold Start Budget: Target < 1s engine availability for start-on-demand at 1000-tenant scale.

## Event Log (Append-Only)

- Records deltas (assert/modify/retract) with timestamps and trace IDs.
- Replay to reconstruct state; supports partial rebuild since last snapshot.
- Throughput: Ensure sustained write throughput compatible with 1000 tenant engines; support log rotation and compression.
- Schema Evolution: Log ruleset version transitions to correlate fact deltas with active rule networks.

## Versioning

- Network has semantic version; rule changes bump version and invalidate old snapshots if incompatible.