# UNIFIED AI OS INTEGRATION

> This document defines the cross-repository integration contract for the Phase 1 unified AI-OS deployment spanning:

- `AETHERIUM-GENESIS`
- `PRGX-AG`


## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Unified AI-OS Integration Guide

This document defines the cross-repository integration contract for the Phase 1 unified AI-OS deployment spanning:

- `AETHERIUM-GENESIS`
- `PRGX-AG`
- `AetherBus-Tachyon`

## Canonical repository roles

| Repository | Canonical role | Runtime responsibility |
| --- | --- | --- |
| `AETHERIUM-GENESIS` | Mind + Body orchestration surface | Intent ingress, directive preparation, manifestation delivery, local service composition |
| `PRGX-AG` | Governance kernel source | Policy evaluation, approval routing, execution gating, risk inspection |
| `AetherBus-Tachyon` | Canonical event bus | Internal ZeroMQ transport, external WebSocket bridge, envelope propagation |

## Cross-repo setup

### 1. Shared protocol contract

All repositories must exchange the same V3 envelope structure:

- `envelope_version=3.0.0`
- `protocol_version=2026.03`
- `correlation_id` created at origin
- `causation_id` preserved across derived events
- `trace_id` preserved across replay and manifestation surfaces
- `origin`, `target`, `topic`, `payload`, `governance`, `memory`, `timestamps`, `content`

See also:
- `docs/directive_envelope_standard.md`
- `docs/AETHERBUS_TACHYON_INTEGRATION.md`

### 2. Runtime endpoint contract

| Variable | Default | Used by |
| --- | --- | --- |
| `BUS_IMPLEMENTATION` | `tachyon` | AETHERIUM-GENESIS |
| `BUS_INTERNAL_ENDPOINT` | `tcp://127.0.0.1:5555` | AETHERIUM-GENESIS + AetherBus-Tachyon |
| `BUS_EXTERNAL_ENDPOINT` | `ws://127.0.0.1:5556/ws` | AETHERIUM-GENESIS + external UI consumers |
| `AETHERBUS_TACHYON_INTERNAL_ENDPOINT` | alias | Cross-repo deployment templates |
| `AETHERBUS_TACHYON_EXTERNAL_ENDPOINT` | alias | Cross-repo deployment templates |

### 3. Recommended startup order

1. Start `AetherBus-Tachyon` internal/external bridge endpoints.
2. Start `PRGX-AG` governance services with access to the same envelope schema and correlation policy.
3. Start `AETHERIUM-GENESIS` with `BUS_IMPLEMENTATION=tachyon`.
4. Attach UI/ope

*[truncated — see source for full prompt]*