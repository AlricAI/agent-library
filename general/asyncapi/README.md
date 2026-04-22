# Asyncapi

> Ratatoskr automatically generates an [AsyncAPI](https://www.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AsyncAPI

Ratatoskr automatically generates an [AsyncAPI](https://www.asyncapi.com/) document from your channel and message configuration. This provides a machine-readable specification of your messaging API — useful for documentation, code generation, and integration with tools like [EventCatalog](https://www.eventcatalog.dev/).

## Setup

Configure the AsyncAPI document metadata:

[!code-csharp[](../examples/Docs/Program.cs#ConfigureAsyncApi)]

Map the AsyncAPI endpoint:

[!code-csharp[](../examples/Docs/Program.cs#MapAsyncApi)]

The document is available at `/asyncapi/asyncapi.json`.

## Automatic Generation

The AsyncAPI document is generated from your channel configuration at runtime. Each channel, message type, and transport binding is reflected automatically:

- **Channels** → AsyncAPI channels with publish/subscribe operations
- **Message types** → AsyncAPI messages with JSON Schema payloads
- **RabbitMQ configuration** → AsyncAPI RabbitMQ bindings (exchange type, queue name, routing key)
- **CloudEvents mode** → Content type and header bindings

No manual annotation is required for basic documentation. Your `AddRatatoskr` configuration is the single source of truth.

## Message Annotations

For richer documentation, annotate messages with `[AsyncApiMessage]` or the fluent API:

### Attribute-Based

```csharp
[RatatoskrMessage("order.placed")]
[AsyncApiMessage(Title = "Order Placed", Summary = "Published when a new order is created")]
public record OrderPlaced(Guid OrderId, string CustomerEmail, decimal Total);
```

### Fluent API

```csharp
bus.AddEventPublishChannel("orders.events", c => c
    .WithRabbitMq(r => r.WithTopicExchange())
    .Produces<OrderPlaced>(m => m
        .WithAsyncApi(api => api
            .WithTitle("Order Placed")
            .WithSummary("Published when a new order is created")
            .WithVersion("1.0.0"))));
```

### Channel and Operation Annotations

```csharp
bus.AddEventPublishChannel("orders.events", c => c
    .WithA

*[truncated — see source for full prompt]*