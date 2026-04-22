# Messages Handlers

> Messages are the data contracts that flow through Ratatoskr.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Messages & Handlers

Messages are the data contracts that flow through Ratatoskr. Handlers are the classes that process them. This page covers how to define messages, register handlers, access message metadata, and customize serialization.

## Defining Messages

A message is any .NET class or record decorated with `[RatatoskrMessage]`. The attribute sets the CloudEvents `type` used for routing:

[!code-csharp[](../examples/Docs/Messages/OrderPlaced.cs#OrderPlaced)]

The type string (e.g., `"order.placed"`) is used as:

- The CloudEvents `type` attribute
- The default RabbitMQ routing key
- The key for resolving handlers in the `ChannelRegistry`

> [!TIP]
> Use dot-separated, lowercase type names following a `{domain}.{event}` or `{domain}.{action}` convention. This aligns with CloudEvents best practices and maps naturally to RabbitMQ topic routing keys.

### Events vs. Commands

Ratatoskr distinguishes between events and commands at the channel level, not the message level. The same message class can be published on an event channel or a command channel. The distinction affects topology ownership:

- **Events** describe something that happened. The producer owns the exchange.
- **Commands** request an action. The consumer owns the exchange.

See [Channels & Routing](channels-routing.md) for details on ownership rules.

## Implementing Handlers

Handlers implement `IMessageHandler<T>` and are resolved from the DI container:

[!code-csharp[](../examples/Docs/Handlers/ProcessPaymentHandler.cs#ProcessPaymentHandler)]

Each handler receives:

- **`message`** — The deserialized message object
- **`properties`** — CloudEvents metadata (ID, source, type, timestamp, trace context, and extension attributes)
- **`cancellationToken`** — Triggered on application shutdown or handler timeout (if configured)

## Registering Handlers

Handlers are registered inside the `Consumes<T>()` builder on a consume channel. There are two registration modes:

### Fire-and-Forget

```csharp
b

*[truncated — see source for full prompt]*