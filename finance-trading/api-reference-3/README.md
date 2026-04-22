# API REFERENCE

> > Complete endpoint reference for the Crypto Vision API.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# API Reference

> Complete endpoint reference for the Crypto Vision API. OpenAPI 3.1 spec at [`openapi.yaml`](../openapi.yaml). Live directory at `GET /api`.

## Base URL

```
Production:  https://cryptocurrency.cv
Development: http://localhost:8080
```

## Authentication

Optional API key authentication via header or query parameter:

```
X-API-Key: your-key-here
# or
GET /api/coins?api_key=your-key-here
```

Admin endpoints require an admin key (set via `ADMIN_API_KEYS` env var).

## Response Format

All responses follow a standard envelope:

```json
{
  "data": { ... },
  "meta": {
    "requestId": "uuid",
    "timestamp": "2026-03-04T00:00:00.000Z",
    "cached": true,
    "source": "coingecko"
  },
  "error": null
}
```

Error responses:

```json
{
  "data": null,
  "meta": { "requestId": "uuid", "timestamp": "..." },
  "error": {
    "code": "RATE_LIMITED",
    "message": "Too many requests",
    "status": 429
  }
}
```

## Rate Limiting

**200 requests per minute per IP** on all `/api/*` routes. Redis-backed when available, in-memory otherwise.

Response headers:
```
X-RateLimit-Limit: 200
X-RateLimit-Remaining: 187
X-RateLimit-Reset: 1709510460
```

---

## Meta Endpoints

### `GET /`

API root with version info and links.

### `GET /health`

Health check with system diagnostics.

**Response:**
```json
{
  "status": "ok",
  "uptime": 123456,
  "cache": { "hits": 5000, "misses": 200, "size": 1500 },
  "circuitBreaker": { "state": "closed", "failures": 0 },
  "websocket": { "clients": 42, "messagesPerSecond": 15 },
  "memory": { "heapUsed": 128000000, "rss": 256000000 }
}
```

### `GET /api`

JSON directory of all available endpoints (300+).

### `GET /api/ready`

Kubernetes readiness probe. Returns 200 when ready, 503 when not.

### `GET /metrics`

Prometheus-format metrics (request counts, latencies, error rates, cache stats).

---

## Market Data

### `GET /api/coins`

Top coins ranked by market cap.

| Parameter | Type | Default | Description |
|---|---|-

*[truncated — see source for full prompt]*