---
name: Event Driven Agent Streaming
description: ## Goal

Real-time, cross-machine agent communication via Apache Pulsar — enabling reactive workflows where agents publish decisions/observations and 
model: claude-sonnet-4-5
---
# Event-Driven Agent Streaming (Apache Pulsar)

## Goal

Real-time, cross-machine agent communication via Apache Pulsar — enabling reactive workflows where agents publish decisions/observations and others respond instantly.

## Why Pulsar Over Kafka

| Factor | Kafka | Pulsar |
|--------|-------|--------|
| Multi-tenancy | Bolt-on (topic naming) | Native (tenants/namespaces) |
| Pub/Sub + Queuing | Pub/sub only, needs separate queue | Unified in one system |
| Geo-replication | MirrorMaker (complex) | Built-in, per-topic |
| Tiered storage | Requires config | Native, auto-offload |
| Operational weight | ZooKeeper (being removed) | BookKeeper (simpler for small clusters) |

## Architecture

```
Agent A (Machine 1)          Agent B (Machine 2)
    │                              │
    ▼                              ▼
┌──────────┐                ┌──────────┐
│ Pulsar   │◄──────────────►│ Pulsar   │
│ Producer │  Pulsar Broker  │ Consumer │
└──────────┘                └──────────┘
                │
        ┌───────┴───────┐
        │  BookKeeper   │
        │  (storage)    │
        └───────────────┘
```

### Topic Hierarchy (Aligned with Memory Tenancy)

```
persistent://global/agents/decisions        ← all agents subscribe
persistent://tenant-{project}/agents/events ← project-scoped
persistent://private-{agent}/internal       ← single agent queues
```

## Use Cases

1. **Reactive workflows**: Security agent publishes vulnerability finding → remediation agent auto-triggers
2. **Real-time handoffs**: Replace polling-based `cross_agent_context.py pending` with push notifications
3. **Event sourcing**: Complete audit log of all agent actions across machines
4. **Load distribution**: Multiple agents subscribe to a shared task queue (competing consumers)

## Integration with Current System

| Current (Qdrant) | Future (Qdrant + Pulsar) |
|---|---|
| `store` → write to Qdrant | `store` → write to Qdrant + publish event to Pulsar |
| `pending` → poll Qdrant | `pending` → Pulsar subscription (push) |
| `broadcast` → write to Qdrant | `broadcast` → Pulsar fanout topic |
| `sync` → query Qdrant | `sync` → replay Pulsar topic from offset |

**Key principle**: Qdrant remains the memory store. Pulsar is the notification/streaming layer. They complement, not replace.

## Implementation Phases

### Phase 1: Local Single-Node
- Docker-based Pulsar standalone for development
- `execution/pulsar_bridge.py` — publish/subscribe wrapper
- Hook into `memory_manager.py` to emit events on store

### Phase 2: Multi-Machine
- Pulsar cluster across machines (2-3 brokers)
- Tenant-scoped namespaces aligned with blockchain ACLs
- Replace polling in `cross_agent_context.py` with subscriptions

### Phase 3: Reactive Workflows
- Define trigger rules in `data/reactive_rules.json`
- Agent auto-responds to events matching its rules
- Dead-letter topics for failed processing

## Prerequisites

- Docker (for Pulsar standalone)
- Blockchain Agent Trust (Phase 2 of that directive — for tenant alignment)