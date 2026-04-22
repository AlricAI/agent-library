# Testing

> The `Ratatoskr.Testing` package provides pipeline observability, parallel test isolation via W3C trace IDs, and ergonomic assertion APIs.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Testing

The `Ratatoskr.Testing` package provides pipeline observability, parallel test isolation via W3C trace IDs, and ergonomic assertion APIs. It has zero overhead in production — the observer collection is empty when not registered.

## Setup

Install the package and register it in your test setup:

```bash
dotnet add package Ratatoskr.Testing
```

```csharp
services.AddRatatoskrTesting();
```

This registers a `MessageTracker` singleton that observes all message activities flowing through the pipeline.

## Session-Based API

The primary API creates a `MessageTrackingSession` per test. Each session generates a unique W3C trace ID that correlates all messages published within its scope — enabling **parallel test isolation**.

```csharp
[Test]
public async Task OrderPlaced_HandlerProcessesSuccessfully()
{
    await using var session = Services.CreateTrackingSession();

    await InScopeAsync(async ctx =>
    {
        var bus = ctx.ServiceProvider.GetRequiredService<IRatatoskr>();
        await bus.PublishDirectAsync(new OrderPlaced(Guid.NewGuid(), "test@example.com", 99.99m));
    });

    var dispatched = await session.WaitForDispatched<OrderPlaced>();
    dispatched.GetMessage<OrderPlaced>().CustomerEmail.Should().Be("test@example.com");
    dispatched.Result.Should().Be(DispatchResult.Success);
}
```

### Creating a Session

```csharp
// From IServiceProvider
await using var session = services.CreateTrackingSession();

// From IHost
await using var session = host.CreateTrackingSession();

// With custom default timeout
await using var session = services.CreateTrackingSession(
    defaultTimeout: TimeSpan.FromSeconds(30));
```

### Waiting for Messages

Each wait method blocks until a matching message arrives or the timeout expires:

```csharp
var published = await session.WaitForPublished<OrderPlaced>();
var sent = await session.WaitForSent<OrderPlaced>();
var received = await session.WaitForReceived<OrderPlaced>();
var dispatched = await session.WaitForDis

*[truncated — see source for full prompt]*