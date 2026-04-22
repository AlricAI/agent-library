# TROUBLESHOOTING

> > Common issues, diagnostic procedures, and solutions for the Crypto Vision platform.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Troubleshooting

> Common issues, diagnostic procedures, and solutions for the Crypto Vision platform.

---

## Table of Contents

- [Quick Diagnostics](#quick-diagnostics)
- [Startup Issues](#startup-issues)
- [Data Source Issues](#data-source-issues)
- [Redis Issues](#redis-issues)
- [BigQuery Issues](#bigquery-issues)
- [AI Provider Issues](#ai-provider-issues)
- [Worker Issues](#worker-issues)
- [WebSocket Issues](#websocket-issues)
- [Performance Issues](#performance-issues)
- [Docker / Container Issues](#docker--container-issues)

---

## Quick Diagnostics

### Health Check

```bash
curl http://localhost:8080/health | jq .
```

The health endpoint provides a comprehensive system overview including:
- Cache statistics (size, hit rate, evictions)
- Circuit breaker states (CLOSED/HALF-OPEN/OPEN per upstream host)
- Queue status (pending, active, total executed)
- WebSocket connections (per topic)
- Degraded routes (routes using fallback sources)
- Memory usage

### Prometheus Metrics

```bash
curl http://localhost:8080/metrics
```

Look for:
- `http_requests_total{status="500"}` — Internal errors
- `upstream_requests_total{status="429"}` — Rate limit hits
- `circuit_breaker_state` — Open circuit breakers (value = 1)
- `queue_depth` — Queue saturation

### Logs

```bash
# Real-time log following
docker logs -f crypto-vision

# Filter errors only
docker logs crypto-vision 2>&1 | grep '"level":"error"'

# Check for slow requests
docker logs crypto-vision 2>&1 | grep "Slow request"
```

---

## Startup Issues

### Environment Validation Failures

**Symptom:** Process crashes immediately on startup with a Zod validation error.

**Cause:** Missing or invalid environment variables. The `env.ts` module validates all required variables at startup.

**Example error:**
```
ZodError: [
  { "code": "invalid_type", "expected": "string", "path": ["DATABASE_URL"] }
]
```

**Solution:** Set the required environment variable:

```bash
# Check what env vars are expected
grep -r '

*[truncated — see source for full prompt]*