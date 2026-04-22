# Operations

> This page covers day-to-day operational concerns: monitoring, handling failures, data retention, distributed lock providers, and deployment considerations.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Operations

This page covers day-to-day operational concerns: monitoring, handling failures, data retention, distributed lock providers, and deployment considerations.

## Monitoring

### Key Metrics

Ratatoskr exposes OpenTelemetry metrics via `System.Diagnostics.Metrics`. See [Observability](observability.md) for the complete metrics reference and setup.

| Metric | Type | Alert Threshold |
|--------|------|-----------------|
| `ratatoskr.outbox.process.count` | Counter | High failure rate |
| `ratatoskr.outbox.poison.count` | Counter | Any increment |
| `ratatoskr.outbox.batch.size` | Histogram | Sustained high values (backlog) |
| `ratatoskr.outbox.process.duration` | Histogram | > 30s |
| `ratatoskr.inbox.deliver.count` | Counter | High failure rate |
| `ratatoskr.inbox.poison.count` | Counter | Any increment |
| `ratatoskr.inbox.batch.size` | Histogram | Sustained high values (backlog) |
| `ratatoskr.inbox.process.duration` | Histogram | > 30s |
| `ratatoskr.lock.acquisition.failure` | Counter | Sustained failures |
| `ratatoskr.lock.lost` | Counter | Any increment |
| `ratatoskr.receive.lag` | Histogram | Growing lag |
| `ratatoskr.process.lag` | Histogram | Growing lag |

### Critical Alerts

1. **Poison count > 0** — Any poisoned message requires investigation
2. **Lock lost** — Indicates infrastructure issues (database connection drops, network partitions)
3. **Growing backlog** — If batch size consistently equals `BatchSize`, the processor cannot keep up
4. **Receive/process lag trending up** — Throughput is insufficient for message volume

### Health Checks

Ratatoskr exposes ASP.NET Core health checks suitable for Kubernetes liveness and readiness probes.

Register them explicitly per component:

```csharp
services.AddHealthChecks()
    .AddRatatoskrRabbitMq()
    .AddRatatoskrOutbox<AppDbContext>()
    .AddRatatoskrInbox<AppDbContext>();
```

**Probes:**
- **Readiness Probe (`"ready"` tag)**: By default, all Ratatoskr components include the `"ready"`

*[truncated — see source for full prompt]*