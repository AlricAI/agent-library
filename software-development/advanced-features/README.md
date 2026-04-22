# ADVANCED FEATURES

> This document covers advanced qtests features that require detailed configuration or have complex use cases.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Advanced Features Documentation

This document covers advanced qtests features that require detailed configuration or have complex use cases.

## 🔄 Error Handling System

The error handling system provides comprehensive error management with context preservation, fallback mechanisms, and integration with monitoring systems.

### Core Error Handling Functions

```typescript
import { handleError, handleAsyncError } from 'qtests/lib/errorHandling.js';

// Basic error handling
handleError(error, 'user-registration', {
  logToConsole: true,
  includeStack: true,
  context: { userId: '123', action: 'register' }
});

// Async error handling with fallback
const user = await handleAsyncError(
  fetchUser('123'), 
  'user-fetch',
  { 
    fallbackValue: null,
    context: { userId: '123' },
    onRetry: (attempt) => console.log(`Retry attempt ${attempt}`)
  }
);
```

### Error Handling Options

| Option | Type | Default | Description |
|--------|------|----------|-------------|
| `logToConsole` | boolean | true | Log errors to console |
| `includeStack` | boolean | true | Include stack trace in logs |
| `context` | object | {} | Additional context data |
| `fallbackValue` | any | undefined | Value to return on error |
| `fallbackMessage` | string | undefined | Custom error message |
| `onRetry` | function | undefined | Callback on retry attempts |

## 🔗 Circuit Breaker Implementation

Production-ready circuit breaker using Opossum library with enterprise features.

### Circuit Breaker Setup

```typescript
import { createCircuitBreaker } from 'qtests/lib/circuitBreaker.js';

// Basic circuit breaker
const breaker = createCircuitBreaker(
  async (data) => externalService.process(data),
  {
    timeout: 5000,                    // 5 second timeout
    errorThresholdPercentage: 50,       // Open at 50% error rate
    resetTimeout: 30000,              // 30 second reset timeout
    monitoring: {
      log: console.info,
      metrics: true                   // Enable metrics c

*[truncated — see source for full prompt]*