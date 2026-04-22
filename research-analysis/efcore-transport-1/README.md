# Efcore Transport

> The EF Core transport delivers messages via the database instead of a message broker.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# EF Core Transport

The EF Core transport delivers messages via the database instead of a message broker. Messages are written directly to inbox tables, making it ideal for single-service applications, development environments, or scenarios where running a broker is not practical.

> [!IMPORTANT]
> The EF Core transport is a **delivery mechanism** — it moves messages from publisher to consumer via the database. It is separate from EF Core **durability** (outbox/inbox patterns). You can use the EF Core transport without an outbox, and you can use the outbox with RabbitMQ instead of the EF Core transport. These are independent choices.

## When to Use

| Use EF Core Transport When | Use RabbitMQ When |
|----------------------------|-------------------|
| Single service, no broker needed | Multiple services communicating |
| Development/testing environment | Production with high throughput |
| Messages stay within one application | Cross-service messaging required |
| Simplest possible setup | Advanced routing (topic, fanout) needed |

## Setup

The EF Core transport requires inbox configuration because messages are delivered by writing directly to inbox tables:

```csharp
builder.Services.AddRatatoskr(bus =>
{
    bus.AddEfCoreDurability<OrderDbContext>(d =>
    {
        d.UseOutbox();
        d.UseInbox();
    });

    // Publish channel with EF Core transport
    bus.AddEventPublishChannel("orders.events", c => c
        .WithEfCore()
        .Produces<OrderPlaced>());

    // Consume channel with inbox
    bus.AddEventConsumeChannel("orders.events", c => c
        .Consumes<OrderPlaced>(m => m
            .WithHandler<OrderPlacedHandler>("order-handler"))
        .UseInbox<OrderDbContext>());
});
```

The DbContext must implement both `IOutboxDbContext` and `IInboxDbContext`:

[!code-csharp[](../examples/Docs/Data/OrderDbContext.cs#OrderDbContext)]

## How It Works

The EF Core transport has no in-memory channel, no consumer loop, and no polling for new messages 

*[truncated — see source for full prompt]*