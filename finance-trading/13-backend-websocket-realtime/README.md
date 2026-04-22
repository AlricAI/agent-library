# 13 Backend Websocket Realtime

> ## Context

You are working on the real-time data layer of crypto-vision. The API server (port 8080) has WebSocket support:

- `src/routes/ws.ts` — We

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 13 — Backend: WebSocket & Real-Time Feeds

## Context

You are working on the real-time data layer of crypto-vision. The API server (port 8080) has WebSocket support:

- `src/routes/ws.ts` — WebSocket route handler
- `src/lib/ws.ts` — WebSocket management utilities
- `@hono/node-ws` — Hono WebSocket adapter
- `ws` — Node.js WebSocket library

The dashboard at `apps/dashboard/` needs live data. The data workers in `src/workers/` periodically fetch fresh data. The connection between workers → WebSocket → dashboard clients needs to be solid.

## Task

### 1. Complete the WebSocket Server (`src/routes/ws.ts`)

Implement a production WebSocket server:

```typescript
// WebSocket endpoint: ws://localhost:8080/ws
//
// Client subscribes by sending:
//   { "type": "subscribe", "channels": ["prices", "trades", "news", "alerts", "gas"] }
//   { "type": "unsubscribe", "channels": ["news"] }
//   { "type": "ping" }
//
// Server sends:
//   { "type": "price", "data": { "bitcoin": { "usd": 65000, "change24h": 2.5 }, ... } }
//   { "type": "trade", "data": { "exchange": "binance", "pair": "BTC/USDT", "price": 65000, ... } }
//   { "type": "news", "data": { "title": "...", "source": "...", "url": "..." } }
//   { "type": "alert", "data": { "coinId": "bitcoin", "type": "price_above", "value": 65000 } }
//   { "type": "gas", "data": { "eth": { "slow": 10, "standard": 15, "fast": 25 } } }
//   { "type": "pong" }
//   { "type": "error", "message": "Unknown channel: foo" }
//
// Features:
//   - Per-client channel subscriptions
//   - Heartbeat: server sends ping every 30s, client must respond within 10s
//   - Auto-disconnect stale clients
//   - Connection auth: optional API key in query param or first message
//   - Rate limit: max 100 messages/min from client
//   - Backpressure: drop messages if client buffer is full
```

### 2. Create the Channel Manager (`src/lib/ws-channels.ts`)

```typescript
// ChannelManager manages WebSocket subscriptions and message routing
//
// C

*[truncated — see source for full prompt]*