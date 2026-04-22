# Outbox

> The transactional outbox pattern solves the dual-write problem: how do you persist business data and publish a message atomically?

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Outbox

The transactional outbox pattern solves the dual-write problem: how do you persist business data and publish a message atomically? Without an outbox, a crash between `SaveChangesAsync()` and `PublishAsync()` means the message is lost even though the data was saved.

Ratatoskr's outbox stages messages in the same database transaction as your business data. A background processor then delivers them to the configured transports.

## Setup

### 1. Configure Durability

```csharp
builder.Services.AddRatatoskr(bus =>
{
    bus.AddEfCoreDurability<OrderDbContext>(d =>
    {
        d.UseOutbox();
    });

    bus.AddEventPublishChannel("orders.events", c => c
        .WithRabbitMq(r => r.WithTopicExchange())
        .Produces<OrderPlaced>());
});
```

### 2. Implement `IOutboxDbContext`

Your `DbContext` must implement `IOutboxDbContext` and register Ratatoskr's EF model (inbox and outbox mappings) in `OnModelCreating`:

```csharp
public class OrderDbContext(DbContextOptions<OrderDbContext> options)
    : DbContext(options), IOutboxDbContext
{
    public OutboxStagingCollection OutboxMessages { get; } = new();

    protected override void OnModelCreating(ModelBuilder modelBuilder)
    {
        modelBuilder.AddRatatoskrEfCoreModel(Database);
    }
}
```

### 3. Register the Outbox Interceptor

In your `DbContext` configuration, register the outbox interceptor:

[!code-csharp[](../examples/Docs/Program.cs#ConfigureDbContext)]

The `RegisterOutbox<TDbContext>(sp)` call adds an EF Core `SaveChanges` interceptor that processes staged messages during `SaveChangesAsync()`.

## Usage

Stage messages using `OutboxMessages.Add()` and call `SaveChangesAsync()`. The message is persisted in the same transaction as your business data:

[!code-csharp[](../examples/Docs/Program.cs#PublishOutboxExample)]

The `OutboxTriggerInterceptor` hooks into `SaveChangesAsync` to:

1. Enrich the message with CloudEvents properties (ID, timestamp, trace context)
2. Serialize the message body

*[truncated — see source for full prompt]*