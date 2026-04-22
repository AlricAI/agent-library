# Openrouter Integration

> This document describes the OpenRouter SDK integration layer used throughout or3-chat.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# OpenRouter Integration

This document describes the OpenRouter SDK integration layer used throughout or3-chat.

## Overview

or3-chat uses the official `@openrouter/sdk` package for non-streaming API calls, with a thin adapter layer in `shared/openrouter/` that provides:

-   Consistent client initialization
-   Normalized error handling
-   Type mapping between SDK types and internal types

## Architecture

```
shared/openrouter/
├── index.ts           # Barrel exports
├── client.ts          # SDK client factory + request options
├── errors.ts          # Error normalization (SDK → NormalizedError)
├── types.ts           # Type mapping (SDK Model → OpenRouterModel)
└── parseOpenRouterSSE.ts  # SSE parsing for streaming (raw fetch)
```

## Usage

### Creating a Client

```ts
import {
    createOpenRouterClient,
    getRequestOptions,
} from '~~/shared/openrouter';

const client = createOpenRouterClient({ apiKey: userKey });

// With common headers (referer, title)
const models = await client.models.list({}, getRequestOptions());

// With abort signal
const response = await client.chat.send(params, getRequestOptions(signal));
```

### Error Handling

```ts
import { normalizeSDKError } from '~~/shared/openrouter';

try {
    await client.models.list({}, getRequestOptions());
} catch (error) {
    const normalized = normalizeSDKError(error);

    console.log(normalized.code); // 'ERR_AUTH', 'ERR_RATE_LIMIT', etc.
    console.log(normalized.message); // User-friendly message
    console.log(normalized.status); // HTTP status code
    console.log(normalized.retryable); // Whether retry makes sense
}
```

### Error Codes

| Code              | HTTP Status | Description                | Retryable |
| ----------------- | ----------- | -------------------------- | --------- |
| `ERR_AUTH`        | 401         | Invalid or expired API key | No        |
| `ERR_CREDITS`     | 402         | Insufficient credits       | No        |
| `ERR_FORBIDDEN`   | 403         | Access deni

*[truncated — see source for full prompt]*