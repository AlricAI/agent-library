# Agent Events

> > **Optional add-on** — works with team/pro modes.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Real-Time Agent Events (Apache Pulsar)

> **Optional add-on** — works with team/pro modes. Without Pulsar, agents poll Qdrant on each query (which always works). Pulsar adds real-time push notifications.

## Why Pulsar?

Without Pulsar, agent coordination works like this: Agent A stores a decision in Qdrant. Agent B doesn't know about it until it runs `memory_manager.py auto`, which queries Qdrant. This is fine for most workflows — Qdrant queries take <10ms.

But in real-time collaboration (e.g., Agent A is writing code while Agent B reviews architecture), the polling delay means Agent B might not see Agent A's latest decisions until its next query. Pulsar fixes this by pushing events to subscribed agents immediately.

### Why Pulsar Over Alternatives?

| Technology | Pros | Cons | Why Not |
|---|---|---|---|
| **Redis Pub/Sub** | Simple, low latency | No persistence, messages lost if subscriber offline | Lost events = lost coordination |
| **RabbitMQ** | Mature, well-supported | Not designed for multi-tenant topics | Topic-per-project pattern is awkward |
| **Kafka** | Excellent persistence | Heavy (ZooKeeper required), overkill for events | 4+ containers for a message bus |
| **Apache Pulsar** | ✅ Topic-per-project, persistent, single container, lightweight standalone mode | Newer ecosystem | — |

**Decision:** Pulsar in standalone mode runs as a single Docker container (256-512MB heap) and natively supports our topic pattern (`persistent://agi/memory/<project>`). Messages persist until consumed. No ZooKeeper, no cluster overhead.

## Architecture

```
Agent A (Machine 1)              Agent B (Machine 2)
  │                                │
  │ store --project myapp          │
  │ → Qdrant (always)             │
  │ → Pulsar event ─────────────→ │ real-time notification
  │                                │ → re-queries Qdrant
  │                                │
  └─── Topic: persistent://agi/memory/myapp ───┘
```

Events are **fire-and-forget** — if Pulsar is d

*[truncated — see source for full prompt]*