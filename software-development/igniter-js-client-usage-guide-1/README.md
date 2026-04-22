# Igniter.js Client Usage Guide

> description: | Comprehensive guide to using the Igniter.js Client, covering server-side and client-side usage patterns, React hooks (useQuery, useMutation, useRealtime), context management, realtime features, and best practices.

## Tags
`typescript` `react`

## System Prompt
---
description: |
  Comprehensive guide to using the Igniter.js Client, covering server-side and client-side usage patterns,
  React hooks (useQuery, useMutation, useRealtime), context management, realtime features, and best practices.
  This rule explains the universal client architecture and how it works seamlessly across different Next.js environments.
alwaysApply: true
priority: 2
---

# Igniter.js Client Usage Guide

This rule provides comprehensive guidance on using the Igniter.js Client, which offers universal type-safe API communication across server and client environments with advanced features like real-time updates, caching, and React hooks integration.

## 1. Universal Client Architecture

### 1.1 Environment-Aware Client

The Igniter.js client automatically adapts to different execution environments:

```typescript
// Generated client file: src/igniter.client.ts
export const api = createIgniterClient<AppRouterType>({
  baseURL: process.env.NEXT_PUBLIC_IGNITER_API_URL || 'http://localhost:3000',
  basePATH: process.env.NEXT_PUBLIC_IGNITER_API_BASE_PATH || '/api/v1',
  router: () => {
    if (typeof window === 'undefined') {
      // Server-side: Direct router access (zero HTTP overhead)
      return require('./igniter.router').AppRouter
    }
    // Client-side: HTTP-based client with hooks
    return require('./igniter.schema').AppRouterSchema
  },
})
```

### 1.2 Execution Environments

**Server-Side Execution (RSC, API Routes, Middleware):**
- Direct function calls via `router.caller`
- Zero HTTP overhead
- Full access to server context
- Synchronous execution model

**Client-Side Execution (Browser, Client Components):**
- HTTP requests via fetch API
- React hooks for state management
- Built-in caching and revalidation
- Real-time subscriptions via SSE

## 2. Server-Side Usage Patterns

### 2.1 React Server Components (RSC)

```typescript
// app/users/page.tsx
import { api } from '@/igniter.client'

export default async function UsersPage() {
  //

*[truncated — see source for full prompt]*