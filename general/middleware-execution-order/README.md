# Middleware Execution Order

> This document explains how middleware is executed in Agentic.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Middleware Execution Order

This document explains how middleware is executed in Agentic.NET.

## Key Principle

**Middlewares execute in the order they are registered**, creating a pipeline where each middleware can process the request before and after the next layer.

## How It Works

### Registration

```csharp
var assistant = new AgentBuilder()
    .WithChatClient(chatClient)
    .WithMemory(memory)              // MemoryMiddleware auto-inserted at position 0
    .UseMiddleware(new FirstMw())    // Registered 1st
    .UseMiddleware(new SecondMw())   // Registered 2nd
    .Build();
```

### Execution Order (First to Last)

```
User Input
    ↓
[FirstMw] (registered 1st)
    ↓ calls next() →
[SecondMw] (registered 2nd)
    ↓ calls next() →
[MemoryMiddleware] (auto-inserted at position 0)
    ↓ calls next() →
[LLM Model]
    ↓ returns response
[MemoryMiddleware] (post-processing continues)
    ↓ returns to SecondMw
[SecondMw] (post-processing continues)
    ↓ returns to FirstMw
[FirstMw] (post-processing continues)
    ↓ returns
Final Response to User
```

## Implementation Details

### Pipeline Construction (Agent.cs, lines 95-99)

The middleware pipeline is built using **reverse iteration**:

```csharp
AgentHandler handler = async (ctx, ct) => await _model.CompleteAsync(ctx.WorkingMessages.ToList(), ct);

foreach (var middleware in _middlewares.Reverse())
{
    var next = handler;
    handler = (ctx, ct) => middleware.InvokeAsync(ctx, next, ct);
}
```

This reverse iteration creates a wrapper chain where:
1. Start with the LLM as the innermost handler
2. For each middleware (in reverse order), wrap the current handler
3. Result: First-registered middleware becomes outermost

### Example with Two Middlewares

Given: `[FirstMw, SecondMw]`

After reverse iteration:
```
handler = FirstMw(SecondMw(LLM))
```

When executed:
1. `FirstMw.InvokeAsync()` is called with `next = SecondMw`
2. `FirstMw` can process pre-LLM (before calling `next()`)
3. When `FirstMw` calls `n

*[truncated — see source for full prompt]*