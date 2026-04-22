# CONFIGURATION

> > Complete environment variable reference for the Crypto Vision monorepo.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Configuration

> Complete environment variable reference for the Crypto Vision monorepo.

## Quick Start

```bash
cp .env.example .env
# Edit .env with your API keys
```

Only `PORT` has a default — everything else is optional. The API works with zero configuration (fetches directly from free upstream APIs).

---

## Server & Runtime

| Variable | Default | Required | Description |
|----------|---------|----------|-------------|
| `PORT` | `8080` | No | HTTP server listen port |
| `NODE_ENV` | `development` | No | Runtime environment (`development` / `production`) |
| `LOG_LEVEL` | `info` | No | Pino log level: `trace` / `debug` / `info` / `warn` / `error` / `fatal` |
| `CORS_ORIGINS` | `""` (all) | No | Comma-separated allowed CORS origins |
| `SHUTDOWN_TIMEOUT_MS` | `15000` | No | Graceful shutdown timeout in milliseconds |
| `SECTBOT_ENABLED` | `false` | No | Enable Telegram bot on startup |
| `CRYPTO_VISION_ENABLED` | — | No | Alternative flag to enable bot on startup |

---

## Cache & Database

| Variable | Default | Required | Description |
|----------|---------|----------|-------------|
| `REDIS_URL` | — | No | Redis connection URL. Falls back to in-memory LRU cache |
| `CACHE_MAX_ENTRIES` | `200000` | No | Max in-memory LRU cache entries |
| `DATABASE_URL` | — | Bot only | PostgreSQL connection string for Telegram bot |
| `UPSTASH_REDIS_REST_URL` | — | No | Upstash KV REST URL (dashboard) |
| `UPSTASH_REDIS_REST_TOKEN` | — | No | Upstash KV REST token (dashboard) |
| `KV_REST_API_URL` | — | No | Vercel KV REST URL (news app) |
| `KV_REST_API_TOKEN` | — | No | Vercel KV REST token (news app) |

---

## Authentication & Rate Limiting

| Variable | Default | Required | Description |
|----------|---------|----------|-------------|
| `API_KEYS` | `""` | No | Comma-separated API keys with optional tier: `key1:basic,key2:pro` |
| `ADMIN_API_KEYS` | `""` | No | Comma-separated admin keys for privileged endpoints |
| `ADMIN_API_KEY` | — | No | Single admin key (da

*[truncated — see source for full prompt]*