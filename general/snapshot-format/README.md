# Snapshot Format

> Near-zero cold start by restoring engine state without recompute.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Snapshot Format (Per Tenant)

Near-zero cold start by restoring engine state without recompute.

## Scope

- One snapshot per tenant_id
- Contains: compiled network version ref, WMEs, alpha memories, beta memories, agenda, refraction set

## Layout

- Header (binary or JSON)
  - version :: integer
  - tenant_id :: String.t()
  - ruleset :: {ruleset_id, version}
  - created_at :: DateTime
- Chunks (streamable files or sections)
  - wme.ndjson (or binary rows): {id, type, attrs}
  - alpha.idx (binary): per alpha memory bucketed IDs
  - beta.mem (binary): tokens with bindings (compact form)
  - agenda.bin: activations queue
  - refr.bin: refraction signatures (with TTL timestamps)

## Properties

- Append-only write, atomic finalize via rename
- Backward-compatible with minor versions; strict match on ruleset version
- Checksums per chunk

## Operations

- Save: periodic or on idle-evict; throttle to avoid hot path impact
- Load: validate header, ensure compiled network loaded, map tables into ETS
- GC: keep last N snapshots; prune by age/size

## BSSN Choices

- Start with NDJSON for WMEs; simple binary for queues/sets
- Single-file directory per tenant: `snapshots/<tenant_id>/<ts>/...`
- No compression initially; measure and add later if needed