# 21 Infra Monitoring Metrics

> ## Context

You are working on the observability layer for crypto-vision. The project is a TypeScript crypto data platform:

- **API server**: Hono v4

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 21 — Monitoring, Metrics & Observability

## Context

You are working on the observability layer for crypto-vision. The project is a TypeScript crypto data platform:

- **API server**: Hono v4.7 on Node.js 22, port 8080, 39 route modules, 200+ endpoints
- **Workers**: 15 background workers (market snapshots, DeFi TVL, news aggregation, anomaly detection, etc.)
- **External APIs**: CoinGecko, DeFiLlama, Binance, CryptoCompare, Messari, etc. — all rate-limited
- **Database**: PostgreSQL 16 (Drizzle ORM), Redis 7 (ioredis), BigQuery
- **Infrastructure**: Docker, Kubernetes (GCP Cloud Run), Pub/Sub

Currently, observability is minimal:
- `src/lib/bigquery.ts` has internal `BQMetrics` tracking inserts/errors/latency
- No Prometheus metrics endpoint
- No structured logging (just `console.log`)
- No health check endpoint beyond basic `/`
- No alerting rules

## Task

### 1. Create Prometheus Metrics Module (`src/lib/metrics.ts`)

```typescript
// Use prom-client library
// Export a singleton Registry
// Expose standard metrics:
//
// HTTP Metrics:
//   http_requests_total (counter) — labels: method, route, status_code
//   http_request_duration_seconds (histogram) — labels: method, route
//   http_request_size_bytes (histogram) — labels: method, route
//   http_response_size_bytes (histogram) — labels: method, route
//   http_active_requests (gauge) — labels: method
//
// Data Source Metrics:
//   data_source_requests_total (counter) — labels: source, endpoint, status
//   data_source_request_duration_seconds (histogram) — labels: source, endpoint
//   data_source_cache_hits_total (counter) — labels: source
//   data_source_cache_misses_total (counter) — labels: source
//   data_source_rate_limit_hits_total (counter) — labels: source
//
// Worker Metrics:
//   worker_jobs_total (counter) — labels: worker, status (success/error)
//   worker_job_duration_seconds (histogram) — labels: worker
//   worker_last_run_timestamp (gauge) — labels: worker
//   worker_backlog_

*[truncated — see source for full prompt]*