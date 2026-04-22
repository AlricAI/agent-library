# Middleware Best Practices

> This guide provides practical best practices for building, testing, and deploying middleware in Agentic.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Middleware Best Practices

This guide provides practical best practices for building, testing, and deploying middleware in Agentic.NET.

## Table of Contents

1. [Design Best Practices](#design-best-practices)
2. [Implementation Best Practices](#implementation-best-practices)
3. [Performance Best Practices](#performance-best-practices)
4. [Testing Best Practices](#testing-best-practices)
5. [Monitoring and Debugging](#monitoring-and-debugging)
6. [Common Pitfalls](#common-pitfalls)

---

## Design Best Practices

### 1. Single Responsibility Principle

Each middleware should have ONE reason to change.

```csharp
// ❌ BAD: Too many responsibilities
sealed class SuperMiddleware : IAssistantMiddleware
{
    public async Task<AgentResponse> InvokeAsync(...)
    {
        // Handles auth, logging, caching, rate limiting, etc.
        // 200+ lines of code
        // Hard to test, modify, reuse
    }
}

// ✅ GOOD: Single responsibility
sealed class AuthenticationMiddleware : IAssistantMiddleware
{
    // Only validates credentials - can be understood in 30 seconds
}

sealed class RateLimitingMiddleware : IAssistantMiddleware
{
    // Only enforces rate limits - orthogonal to authentication
}
```

### 2. Design for Composability

Middleware should work well with other middleware, not assume it's alone.

```csharp
// ❌ BAD: Assumes exclusive behavior
sealed class CacheMiddleware : IAssistantMiddleware
{
    private static Dictionary<string, Response> _cache;  // Shared state!
    
    public async Task<AgentResponse> InvokeAsync(...)
    {
        // Cached responses are returned for ANY user
        // But next middleware might be authentication!
    }
}

// ✅ GOOD: Respects other middleware
sealed class CacheMiddleware : IAssistantMiddleware
{
    private readonly Dictionary<string, Response> _cache;
    
    public async Task<AgentResponse> InvokeAsync(...)
    {
        // Authentication runs first, so we know user is verified
        // Rate limiting runs first, so w

*[truncated — see source for full prompt]*