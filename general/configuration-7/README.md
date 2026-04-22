# Configuration

> This page provides a quick-reference index of all configuration options across Ratatoskr.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Configuration Reference

This page provides a quick-reference index of all configuration options across Ratatoskr. Each table links to the feature page where the option is documented in detail.

## Core

```csharp
builder.Services.AddRatatoskr(bus =>
{
    // All configuration happens here
});
```

### Channel Methods

| Method | Intent | Details |
|--------|--------|---------|
| `AddEventPublishChannel(name, ...)` | Publish events you own | [Channels & Routing](channels-routing.md) |
| `AddCommandPublishChannel(name, ...)` | Send commands to others | [Channels & Routing](channels-routing.md) |
| `AddEventConsumeChannel(name, ...)` | Subscribe to others' events | [Channels & Routing](channels-routing.md) |
| `AddCommandConsumeChannel(name, ...)` | Process commands you own | [Channels & Routing](channels-routing.md) |

### Message & Handler Registration

| Method | Description | Details |
|--------|-------------|---------|
| `.Produces<T>()` | Register a message type on a publish channel | [Channels & Routing](channels-routing.md) |
| `.Consumes<T>(m => ...)` | Register a message type and handlers on a consume channel | [Messages & Handlers](messages-handlers.md) |
| `.WithSerializer<TSerializer>()` | Use a serializer for a specific message type | [Messages & Handlers](messages-handlers.md) |
| `.WithHandler<T>()` | Fire-and-forget handler (no persistence) | [Messages & Handlers](messages-handlers.md) |
| `.WithHandler<T>("key")` | Inbox-managed handler with stable key | [Inbox](inbox.md) |
| `.AllowConsumeWithoutInbox()` | Explicit opt-out from optional consume-channel inbox requirement policy | [Inbox](inbox.md) |

### Attributes

| Attribute | Target | Description | Details |
|-----------|--------|-------------|---------|
| `[RatatoskrMessage("type")]` | Class/Record | Sets the CloudEvents `type` and default routing key | [Messages & Handlers](messages-handlers.md) |
| `[AsyncApiMessage(...)]` | Class/Record | Adds AsyncAPI documentation metadata | [AsyncAPI](as

*[truncated — see source for full prompt]*