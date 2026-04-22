# Cloudevents

> Ratatoskr uses the [CloudEvents](https://cloudevents.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CloudEvents

Ratatoskr uses the [CloudEvents](https://cloudevents.io/) specification as its message envelope format. Every message published through Ratatoskr is a CloudEvents v1.0 event with standard attributes for identity, type, source, and trace context. This page covers how CloudEvents maps to Ratatoskr's `MessageProperties`, content modes, and configuration.

## CloudEvents Attributes

When a message is published, Ratatoskr automatically populates these CloudEvents attributes in `MessageProperties`:

| CloudEvents Attribute | `MessageProperties` Property | Source |
|----------------------|------------------------------|--------|
| `id` | `Id` | Auto-generated GUID v7 |
| `source` | `Source` | `ConfigureCloudEvents(ce => ce.DefaultSource = "...")` |
| `type` | `Type` | `[RatatoskrMessage("order.placed")]` attribute |
| `specversion` | (always `"1.0"`) | Hardcoded |
| `time` | `Time` | Current UTC timestamp from `TimeProvider` |
| `datacontenttype` | `DataContentType` | `"application/json"` (default) |
| `dataschema` | `DataSchema` | Optional URI identifying the data schema |

### Data Schema

The optional `dataschema` attribute identifies the schema that the event data adheres to. When present, it must be a valid URI (per the CloudEvents spec).

Configure it per message type via the `[RatatoskrMessage]` attribute:

```csharp
[RatatoskrMessage("order.placed", DataSchema = "https://schemas.example.com/events/order.placed/v1.json")]
public class OrderPlaced { ... }
```

Or via the fluent channel builder:

```csharp
bus.AddEventPublishChannel("orders", c => c
    .Produces<OrderPlaced>(m => m.WithDataSchema("https://schemas.example.com/events/order.placed/v1.json")));
```

You can also set it per-publish via `MessageProperties.DataSchema` (overrides the defaults above):

```csharp
await bus.PublishDirectAsync(orderPlaced, new MessageProperties
{
    DataSchema = "https://schemas.example.com/events/order.placed/v1.json",
});
```

The attribute is preserved in both

*[truncated — see source for full prompt]*