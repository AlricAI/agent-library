# MONITORING

> > Prometheus metrics, structured logging, health checks, and alerting for the Crypto Vision platform.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Monitoring & Observability

> Prometheus metrics, structured logging, health checks, and alerting for the Crypto Vision platform.

---

## Table of Contents

- [Overview](#overview)
- [Prometheus Metrics](#prometheus-metrics)
  - [HTTP Metrics](#http-metrics)
  - [Upstream Metrics](#upstream-metrics)
  - [Cache Metrics](#cache-metrics)
  - [Queue Metrics](#queue-metrics)
  - [Circuit Breaker Metrics](#circuit-breaker-metrics)
  - [WebSocket Metrics](#websocket-metrics)
- [Health Endpoint](#health-endpoint)
- [Structured Logging](#structured-logging)
- [Path Normalization](#path-normalization)
- [Dashboard Setup](#dashboard-setup)
- [Alerting Recommendations](#alerting-recommendations)

---

## Overview

Crypto Vision provides three pillars of observability:

| Pillar | Technology | Endpoint / Config |
|---|---|---|
| **Metrics** | Prometheus (prom-client) | `GET /metrics` |
| **Logging** | Pino (structured JSON) | `LOG_LEVEL` env var |
| **Health** | Custom health check | `GET /health` |

**Source files:**
- `src/lib/metrics.ts` — Prometheus metrics registration and helpers
- `src/lib/middleware.ts` — Request logging, timing, and metrics middleware
- `src/index.ts` — Health endpoint and metric summary

---

## Prometheus Metrics

All metrics are exposed at `GET /metrics` in Prometheus exposition format. Scrape with a standard Prometheus configuration:

```yaml
# prometheus.yml
scrape_configs:
  - job_name: 'crypto-vision'
    scrape_interval: 15s
    static_configs:
      - targets: ['crypto-vision:8080']
```

### HTTP Metrics

| Metric | Type | Labels | Description |
|---|---|---|---|
| `http_requests_total` | Counter | `method`, `path`, `status` | Total HTTP requests |
| `http_request_duration_seconds` | Histogram | `method`, `path`, `status` | Request latency distribution |

**Histogram buckets:** 0.005, 0.01, 0.025, 0.05, 0.1, 0.25, 0.5, 1, 2.5, 5, 10

**Example PromQL queries:**

```promql
# Request rate (per second)
rate(http_requests_total[5m])

# P99 laten

*[truncated — see source for full prompt]*