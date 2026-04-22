# Middleware Composition

> This guide explains how to compose and combine multiple middlewares effectively in Agentic.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Middleware Composition Guide

This guide explains how to compose and combine multiple middlewares effectively in Agentic.NET.

## What is Middleware Composition?

Middleware composition is the art of combining multiple independent middlewares into a cohesive pipeline that works together to achieve complex goals.

Instead of building one large middleware that does everything, you build small, focused middlewares that each do one thing well, then combine them.

## Core Principle: Single Responsibility

Each middleware should do ONE thing:

```csharp
// ❌ BAD: Does too much
sealed class SuperMiddleware : IAssistantMiddleware
{
    public async Task<AgentResponse> InvokeAsync(...)
    {
        // Authentication
        if (!ValidateApiKey(...)) return Error();
        
        // Rate limiting
        if (!CheckRateLimit(...)) return Error();
        
        // Logging
        LogRequest(...);
        
        var response = await next(...);
        
        // Caching
        CacheResponse(...);
        
        // Response filtering
        FilterContent(...);
        
        // Monitoring
        RecordMetrics(...);
        
        LogResponse(...);
        
        return response;
    }
}

// ✅ GOOD: Each middleware has one job
.UseMiddleware(new AuthenticationMiddleware())
.UseMiddleware(new RateLimitingMiddleware())
.UseMiddleware(new LoggingMiddleware())
.UseMiddleware(new CachingMiddleware())
.UseMiddleware(new ResponseFilterMiddleware())
.UseMiddleware(new MonitoringMiddleware())
```

## Building Blocks: Middleware Types

Agentic.NET provides these middleware building blocks:

| Type | Purpose | Pattern | Example |
|------|---------|---------|---------|
| **Gating** | Control access | Short-circuit | Authentication, Rate Limiting |
| **Transformation** | Modify data | Filter | Response filtering, caching |
| **Observation** | Monitor behavior | Filter | Logging, metrics |
| **Enrichment** | Add context | Augmentation | Memory injection, user info |
| **R

*[truncated — see source for full prompt]*