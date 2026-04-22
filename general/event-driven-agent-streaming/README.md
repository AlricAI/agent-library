# Event Driven Agent Streaming

> ## Goal

Real-time, cross-machine agent communication via Apache Pulsar — enabling reactive workflows where agents publish decisions/observations and 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
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
| `pending` → poll Qdrant | `pending` → Puls

*[truncated — see source for full prompt]*