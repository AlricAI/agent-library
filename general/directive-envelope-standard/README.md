# Directive Envelope Standard

> This document defines the canonical directive envelope used to connect Intent, Reasoning, Governance, Execution, Memory commit, and Manifestation.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Directive Envelope Standard (V3)

This document defines the canonical directive envelope used to connect Intent, Reasoning, Governance, Execution, Memory commit, and Manifestation.

## Objectives

- Provide one stable packet shape for cross-subsystem traceability.
- Preserve replayability in Akashic Memory.
- Preserve governance-first execution gates with explicit risk and approval metadata.

## Canonical schema

```json
{
  "envelope_version": "3.0.0",
  "protocol_version": "2026.03",
  "envelope_id": "uuid",
  "type": "intent_detected|manifestation|degradation|...",
  "correlation_id": "uuid-created-at-origin",
  "causation_id": "uuid-or-null",
  "origin": {
    "service": "api|genesis_core|governance|memory|tachyon",
    "subsystem": "body|mind|kernel|memory|bus",
    "instance": "optional-runtime-instance",
    "channel": "session-or-stream-id"
  },
  "target": {
    "service": "client|genesis_core|governance|memory|broadcast",
    "subsystem": "manifestation|mind|kernel|memory|bus",
    "instance": "optional-runtime-instance",
    "channel": "session-or-stream-id"
  },
  "topic": "intent.ingress",
  "payload": {},
  "governance": {
    "decision": "ALLOWED|DENIED|PENDING_APPROVAL|null",
    "risk_tier": "TIER_0..TIER_3|null",
    "policy_effect": "ALLOW|DENY|REQUIRE_APPROVAL|null",
    "policy_mode": "enforce|dry_run",
    "approval_ticket_id": "string|null",
    "validated": true
  },
  "memory": {
    "ledger_event_type": "intent_ingress|governance_allowed|execution_completed|...",
    "ledger_record_id": "string|null",
    "causal_chain": ["uuid"],
    "replayable": true
  },
  "timestamps": {
    "created_at": "2026-03-18T00:00:00+00:00",
    "published_at": "2026-03-18T00:00:00+00:00",
    "consumed_at": "2026-03-18T00:00:00+00:00"
  },
  "content": {
    "content_type": "application/json",
    "content_encoding": "identity",
    "content_compression": "none",
    "codec": "json|msgpack"
  },
  "extensions": {
    "bus_metadata": {
      "codec": "json|m

*[truncated — see source for full prompt]*