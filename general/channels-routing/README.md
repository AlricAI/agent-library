# Channels Routing

> Ratatoskr uses a channel-first design where channels are the primary unit of configuration.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Channels & Routing

Ratatoskr uses a channel-first design where channels are the primary unit of configuration. A channel groups related message types, assigns transport settings, and declares ownership intent. This page covers the channel API, ownership rules, and message routing.

## Channel-First Design

Everything in Ratatoskr starts with a channel. You don't configure messages or handlers in isolation — you attach them to a channel that declares:

1. **Intent** — Are you publishing or consuming? Events or commands?
2. **Transport** — How are messages delivered? (RabbitMQ, EF Core)
3. **Message types** — What messages flow through this channel?
4. **Handlers** — Who processes incoming messages? (consume channels only)

This design centralizes topology decisions and enforces ownership conventions at the API level.

## Channel Types

Ratatoskr provides four channel methods, each encoding a specific intent:

| Method | Intent | You Are | Topology Action (RabbitMQ) |
|--------|--------|---------|---------------------------|
| `AddEventPublishChannel` | Publish events you own | Producer | **Declare** exchange |
| `AddCommandPublishChannel` | Send commands to others | Sender | **Validate** exchange exists |
| `AddEventConsumeChannel` | Subscribe to others' events | Subscriber | **Validate** exchange, **declare** queue, **bind** |
| `AddCommandConsumeChannel` | Process commands you own | Processor | **Declare** exchange + queue |

### Ownership Rules

The key insight is **who owns what**:

- **Event producers** own their exchange. They declare it because they control the schema and topology.
- **Command consumers** own their exchange. They declare it because they define the contract for incoming commands.
- **Event subscribers** and **command senders** only validate that the exchange exists. They don't create it.

This prevents topology conflicts when multiple services share infrastructure.

## Configuration

### Publish Channels

Publish channels declare what messag

*[truncated — see source for full prompt]*