# AETHERBUS TACHYON INTEGRATION

> ## Purpose

This document defines the canonical Phase 1 bus path for AETHERIUM-GENESIS. The platform now treats **AetherBus-Tachyon** as the preferred

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AetherBus-Tachyon Integration Guide

## Purpose

This document defines the canonical Phase 1 bus path for AETHERIUM-GENESIS. The platform now treats **AetherBus-Tachyon** as the preferred runtime transport and keeps legacy in-process bus implementations only as compatibility layers.

Canonical path:

`Intent -> V3 Envelope -> Governance-aware Bus Publish -> Tachyon Internal ZeroMQ -> Tachyon WebSocket Bridge -> Manifestation`

## Runtime topology

### Internal microservices

- Transport: **ZeroMQ PUB/SUB**
- Default endpoint: `tcp://127.0.0.1:5555`
- Use case: internal backend components, lifecycle orchestration, governance telemetry, memory events

### External / UI consumers

- Transport: **WebSocket bridge**
- Default endpoint: `ws://127.0.0.1:5556/ws`
- Use case: dashboards, manifestation surfaces, operator consoles, replay tooling

## Configuration contract

The runtime bus implementation is selected by environment variables.

| Variable | Default | Description |
| --- | --- | --- |
| `BUS_IMPLEMENTATION` | `tachyon` | Runtime selector. Supported values: `tachyon`, `extreme`, `legacy`. |
| `BUS_INTERNAL_ENDPOINT` | `tcp://127.0.0.1:5555` | Internal ZeroMQ endpoint. |
| `AETHERBUS_TACHYON_INTERNAL_ENDPOINT` | _(alias)_ | Alias accepted for cross-repository deployment templates. |
| `BUS_EXTERNAL_ENDPOINT` | `ws://127.0.0.1:5556/ws` | External WebSocket bridge endpoint. |
| `AETHERBUS_TACHYON_EXTERNAL_ENDPOINT` | _(alias)_ | Alias accepted for cross-repository deployment templates. |
| `BUS_CODEC` | `msgpack` | Envelope payload codec (`msgpack` or `json`). |
| `BUS_COMPRESSION` | `none` | Compression metadata for transport coordination. |
| `BUS_TIMEOUT_MS` | `2000` | Publish/receive timeout budget. |
| `BUS_RECONNECT_INITIAL_DELAY_MS` | `250` | First reconnect delay. |
| `BUS_RECONNECT_MAX_DELAY_MS` | `5000` | Maximum reconnect backoff. |
| `BUS_RECONNECT_MAX_ATTEMPTS` | `10` | Maximum reconnect attempts before escalation. |

## Envelope requirements

Every cr

*[truncated — see source for full prompt]*