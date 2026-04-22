# Inbox

> The inbox pattern provides **durable, per-handler delivery** with automatic retry and deduplication.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Inbox

The inbox pattern provides **durable, per-handler delivery** with automatic retry and deduplication. Once a message is accepted into the inbox, each registered handler is invoked at least once per (message ID, handler) pair — surviving application crashes, redeliveries, and concurrent processing. Persisted completion records prevent duplicate deliveries under normal operation.

> [!IMPORTANT]
> **Handlers must be idempotent.** The inbox deduplicates deliveries per (message ID, handler) pair, but does not guarantee exactly-once *processing*. If a handler succeeds but the process crashes before the completion status is persisted, the handler will be re-invoked. Design handlers to produce the same result when called twice — use upserts, check for existing records, or use the message ID as an idempotency key.

## When to Use

Use the inbox when:

- Handler failures must not prevent other handlers from succeeding (per-handler isolation)
- Message processing must survive application crashes without redelivery from the broker
- Deduplication per (message ID, handler) pair is required to minimize duplicate processing
- You want durable retry with backoff instead of relying on the transport's retry mechanism

## Setup

### 1. Configure Durability

[!code-csharp[](../examples/Docs/Program.cs#ConfigureDurability)]

### 2. Implement DbContext Interfaces

Your `DbContext` must implement `IInboxDbContext` (and `IOutboxDbContext` if using the outbox):

[!code-csharp[](../examples/Docs/Data/OrderDbContext.cs#OrderDbContext)]

### 3. Register Handlers with Stable Keys

Handlers on inbox channels must have a stable key:

```csharp
bus.AddEventConsumeChannel("orders.events", c => c
    .WithRabbitMq(r => r
        .WithQueueName("orders.events.subscriptions")
        .WithRetry(maxRetries: 3, delay: TimeSpan.FromSeconds(30)))
    .Consumes<OrderPlaced>(m => m
        .WithHandler<OrderPlacedHandler>("order-handler"))
    .UseInbox<OrderDbContext>());
```

The handler key (`"o

*[truncated — see source for full prompt]*