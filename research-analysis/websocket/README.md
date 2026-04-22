# WEBSOCKET

> > Real-time streaming data via WebSocket connections — prices, Bitcoin network events, DEX trades, and anomaly alerts.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# WebSocket Real-Time Feeds

> Real-time streaming data via WebSocket connections — prices, Bitcoin network events, DEX trades, and anomaly alerts.

---

## Table of Contents

- [Overview](#overview)
- [Connection](#connection)
- [Topics](#topics)
  - [Prices](#prices)
  - [Bitcoin](#bitcoin)
  - [Trades](#trades)
  - [Alerts](#alerts)
- [Message Formats](#message-formats)
- [Architecture](#architecture)
  - [Price Throttling](#price-throttling)
  - [Multi-Instance Fan-Out](#multi-instance-fan-out)
  - [Reconnection](#reconnection)
- [Client Examples](#client-examples)
- [Configuration](#configuration)

---

## Overview

Crypto Vision provides four WebSocket topics for real-time data streaming:

| Topic | Endpoint | Upstream Source | Description |
|---|---|---|---|
| **Prices** | `/ws/prices` | CoinCap | Real-time crypto prices (5 Hz throttled) |
| **Bitcoin** | `/ws/bitcoin` | Mempool.space | Bitcoin blocks, transactions, mempool |
| **Trades** | `/ws/trades` | DexScreener | Live DEX trade events |
| **Alerts** | `/ws/alerts` | Internal | Anomaly detection alerts |

**Source file:** `src/lib/ws.ts` (860 lines)

---

## Connection

### Endpoint Format

```
ws://localhost:8080/ws/{topic}
wss://cryptocurrency.cv/ws/{topic}
```

### Example Connection

```javascript
const ws = new WebSocket('ws://localhost:8080/ws/prices');

ws.onopen = () => console.log('Connected');
ws.onmessage = (event) => {
  const data = JSON.parse(event.data);
  console.log(data);
};
ws.onclose = () => console.log('Disconnected');
ws.onerror = (err) => console.error('Error:', err);
```

### Connection Lifecycle

1. Client connects to a topic endpoint
2. Server registers the client in the topic subscription set
3. If this is the first subscriber for the topic, the upstream WebSocket connection is established
4. Data flows from upstream → server → all subscribed clients
5. When the last client disconnects from a topic, the upstream connection is closed

---

## Topics

### Prices

**Endpoint:** `/

*[truncated — see source for full prompt]*