# RPC USAGE

> This GitHub worker supports full RPC (Remote Procedure Call) capabilities, allowing it to be used as a service binding in other Cloudflare Workers.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# GitHub Worker RPC Usage Guide

This GitHub worker supports full RPC (Remote Procedure Call) capabilities, allowing it to be used as a service binding in other Cloudflare Workers.

## Table of Contents

- [Overview](#overview)
- [Setup](#setup)
- [Available RPC Methods](#available-rpc-methods)
- [Usage Examples](#usage-examples)
- [Type Definitions](#type-definitions)

## Overview

The GitHub worker can be consumed in two ways:

1. **HTTP API** - Traditional REST API endpoints accessible via HTTP requests
2. **RPC Service Binding** - Direct method calls from other workers without HTTP overhead

RPC service bindings provide:
- **Better Performance** - No HTTP serialization/deserialization overhead
- **Type Safety** - Full TypeScript type support
- **Simplified Code** - Direct method calls instead of HTTP requests
- **Lower Latency** - Worker-to-worker communication without network calls

## Setup

### Step 1: Deploy the GitHub Worker

First, ensure the GitHub worker is deployed:

```bash
cd /path/to/github-worker
npm run deploy
```

### Step 2: Configure Service Binding

In your consuming worker's `wrangler.jsonc`, add a service binding:

```jsonc
{
  "name": "my-worker",
  "main": "src/index.ts",
  "services": [
    {
      "binding": "GITHUB_WORKER",
      "service": "core-github-api"
    }
  ]
}
```

**Note**: The `service` value must match the `name` in the GitHub worker's `wrangler.jsonc` (currently `"core-github-api"`).

### Step 3: Add Type Definitions (Optional but Recommended)

For full type safety, copy the RPC type definitions to your project:

```bash
cp /path/to/github-worker/src/rpc/types.ts ./src/types/github-worker-rpc.ts
```

Or install via npm if published as a package.

### Step 4: Update Environment Types

Create or update your worker's environment types:

```typescript
// src/types/env.ts
import type { GitHubWorkerRPC } from './github-worker-rpc'

interface Env {
  GITHUB_WORKER: Service<GitHubWorkerRPC>
  // ... other bindings
}
```

## Availab

*[truncated — see source for full prompt]*