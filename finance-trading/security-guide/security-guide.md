---
name: SECURITY GUIDE
description: > Security architecture, threat mitigations, and best practices for the Crypto Vision platform.
model: claude-sonnet-4-5
---
# Security Guide

> Security architecture, threat mitigations, and best practices for the Crypto Vision platform.

---

## Table of Contents

- [Security Architecture](#security-architecture)
- [Transport Security](#transport-security)
- [Authentication](#authentication)
- [Rate Limiting](#rate-limiting)
- [Input Validation](#input-validation)
- [Output Security](#output-security)
- [HTTP Security Headers](#http-security-headers)
- [CORS Policy](#cors-policy)
- [Secret Management](#secret-management)
- [Error Redaction](#error-redaction)
- [Dependency Security](#dependency-security)
- [Deployment Security](#deployment-security)

---

## Security Architecture

```
Client Request
     │
     ▼
┌────────────────────────────────────────────────────┐
│ Layer 1: Transport (TLS)                           │
│   • HTTPS enforced in production                   │
│   • HSTS with 1-year max-age                       │
└────────────────────┬───────────────────────────────┘
                     │
┌────────────────────▼───────────────────────────────┐
│ Layer 2: HTTP Security Headers                     │
│   • CSP, X-Frame-Options, X-Content-Type-Options   │
│   • Referrer-Policy, Permissions-Policy             │
└────────────────────┬───────────────────────────────┘
                     │
┌────────────────────▼───────────────────────────────┐
│ Layer 3: Body Size Limiting (256KB)                │
│   • Prevents memory exhaustion attacks              │
└────────────────────┬───────────────────────────────┘
                     │
┌────────────────────▼───────────────────────────────┐
│ Layer 4: CORS Validation                           │
│   • Whitelist in production, open in development    │
└────────────────────┬───────────────────────────────┘
                     │
┌────────────────────▼───────────────────────────────┐
│ Layer 5: Rate Limiting (sliding window)            │
│   • Per-IP for anonymous, per-key for authenticated │
│   • Redis backend with Lua atomic operations        │
└────────────────────┬───────────────────────────────┘
                     │
┌────────────────────▼───────────────────────────────┐
│ Layer 6: Authentication (API Key)                  │
│   • Timing-safe comparison to prevent timing attacks│
│   • Tier assignment for quota enforcement            │
└────────────────────┬───────────────────────────────┘
                     │
┌────────────────────▼───────────────────────────────┐
│ Layer 7: Input Validation (Zod schemas)            │
│   • Type coercion, range checks, pattern matching   │
│   • Sanitization of string inputs                    │
└────────────────────┬───────────────────────────────┘
                     │
┌────────────────────▼───────────────────────────────┐
│ Layer 8: Output Security                           │
│   • Source obfuscation (upstream names hidden)       │
│   • Error detail redaction in production             │
│   • Response envelope normalization                  │
└────────────────────────────────────────────────────┘
```

---

## Transport Security

### HTTPS Enforcement

In production, all traffic must use HTTPS. This is enforced at the infrastructure level:

- **Cloud Run / GKE** — TLS termination at the load balancer
- **Self-hosted** — TLS via reverse proxy (Nginx, Caddy, Traefik)

### HSTS (Strict-Transport-Security)

The `secureHeaders()` middleware sets:

```
Strict-Transport-Security: max-age=31536000; includeSubDomains
```

This instructs browsers to always use HTTPS for the domain for 1 year, preventing protocol downgrade attacks.

---

## Authentication

See [API Authentication](API_AUTHENTICATION.md) for the full guide.

**Key security properties:**

- **Timing-safe comparison** — API keys are compared using constant-time comparison (`crypto.timingSafeEqual`) to prevent timing side-channel attacks
- **Key hashing** — Keys stored in Redis can be configured to store only hashes, preventing exposure if Redis is compromised
- **Tier isolation** — Each API key is assigned a tier that determines rate limits and feature access
- **Admin separation** — Admin keys are stored in a separate environment variable (`ADMIN_API_KEYS`) and are never mixed with regular keys

---

## Rate Limiting

### Implementation

Sliding-window rate limiting with dual backend:

1. **Redis** (distributed) — Uses an atomic Lua script for `INCR` → `PEXPIRE` in a single round trip, preventing race conditions
2. **In-memory** (fallback) — `Map<key, {count, windowStart}>` with periodic cleanup when Redis is unavailable

### Limits by Tier

| Tier | Limit | Window | Key Required |
|---|---|---|---|
| `public` | 30 | 60s | No |
| `basic` | 200 | 60s | Yes |
| `pro` | 2,000 | 60s | Yes |
| `enterprise` | 10,000 | 60s | Yes |

### Response Headers

Rate limit status is communicated via standard HTTP headers:

```
X-RateLimit-Limit: 30
X-RateLimit-Remaining: 25
X-RateLimit-Reset: 1709568060
```

On limit exceeded (429):

```
Retry-After: 45
```

### DDoS Mitigation

Rate limiting alone doesn't prevent DDoS attacks. In production, use additional layers:

1. **Cloud Armor / Cloudflare** — Edge-level DDoS protection
2. **IP-based rate limiting** — Applied before API key check
3. **Body size limit** — 256KB prevents memory exhaustion from large payloads

---

## Input Validation

### Zod Schema Validation

All request parameters (query strings, path parameters, request bodies) are validated using Zod schemas before processing:

```typescript
const QuerySchema = z.object({
  coinId: z.string().min(1).max(100).regex(/^[a-z0-9-]+$/),
  vs_currency: z.enum(['usd', 'eur', 'gbp', 'btc', 'eth']).default('usd'),
  days: z.coerce.number().int().min(1).max(365).default(30),
  limit: z.coerce.number().int().min(1).max(250).default(100),
});
```

**Validation patterns used throughout:**

| Pattern | Purpose |
|---|---|
| `z.string().min(1).max(N)` | Bounded string length |
| `z.string().regex(/^[a-z0-9-]+$/)` | Alphanumeric + hyphen only (coin IDs) |
| `z.coerce.number().int().min(1).max(N)` | Bounded integers |
| `z.enum([...])` | Closed set of allowed values |
| `z.string().trim()` | Whitespace stripping |
| `z.string().toLowerCase()` | Case normalization |

### Path Traversal Protection

Any user-supplied path segments are sanitized to prevent directory traversal:

```typescript
// Blocked patterns: ../../, %2e%2e%2f, ..%5c
const sanitized = input.replace(/\.\.[/\\]/g, '');
```

### SQL Injection Protection

All database queries use Drizzle ORM with parameterized queries. No raw SQL strings are constructed from user input.

---

## Output Security

### Source Obfuscation

Upstream provider names (CoinGecko, DeFiLlama, Binance, etc.) are **never** exposed in error responses to clients. This prevents attackers from discovering the exact upstream services and targeting them directly.

The `response-envelope.ts` module maps path segments to generic source names for the `meta.source` field, but error details about specific upstream failures are sanitized before reaching the client.

### Error Detail Redaction

Error responses follow a consistent format that **never** includes:

- Internal stack traces
- Database query details
- Upstream API URLs or headers
- Configuration values or secrets
- File paths or line numbers

**Production error response:**

```json
{
  "success": false,
  "error": {
    "code": "UPSTREAM_ERROR",
    "message": "Data source temporarily unavailable. Please try again."
  }
}
```

**Development error response** (only when `NODE_ENV=development`):

```json
{
  "success": false,
  "error": {
    "code": "UPSTREAM_ERROR",
    "message": "Data source temporarily unavailable. Please try again.",
    "details": {
      "source": "coingecko",
      "status": 429,
      "retryAfter": 60
    }
  }
}
```

---

## HTTP Security Headers

The `secureHeaders()` middleware sets the following headers on all responses:

| Header | Value | Purpose |
|---|---|---|
| `Strict-Transport-Security` | `max-age=31536000; includeSubDomains` | HTTPS enforcement |
| `X-Frame-Options` | `DENY` | Prevents clickjacking |
| `X-Content-Type-Options` | `nosniff` | Prevents MIME type sniffing |
| `X-XSS-Protection` | `1; mode=block` | Legacy XSS filter |
| `Referrer-Policy` | `strict-origin-when-cross-origin` | Limits referrer information |
| `Content-Security-Policy` | `default-src 'self'` | Restricts resource loading |
| `Permissions-Policy` | `geolocation=(), camera=(), microphone=()` | Disables unused browser APIs |

---

## CORS Policy

| Environment | CORS Configuration |
|---|---|
| Development | `origin: *` (all origins allowed) |
| Production | Whitelist via `CORS_ORIGINS` env var |

```bash
# Production CORS configuration
CORS_ORIGINS=https://cryptocurrency.cv,https://dashboard.cryptocurrency.cv,https://www.cryptocurrency.cv
```

The CORS middleware validates:
- `Origin` header against the whitelist
- `Access-Control-Request-Method` for preflight requests
- `Access-Control-Request-Headers` for custom headers (e.g., `X-API-Key`)

---

## Secret Management

### Environment Variables

All secrets are loaded from environment variables — **never** hardcoded:

| Secret | Env Var | Required |
|---|---|---|
| API keys (static) | `API_KEYS` | No |
| Admin API keys | `ADMIN_API_KEYS` | No |
| Redis password | `REDIS_URL` (embedded) | No |
| PostgreSQL password | `DATABASE_URL` (embedded) | No |
| AI provider keys | `GROQ_API_KEY`, `OPENAI_API_KEY`, etc. | No (per provider) |
| BigQuery credentials | `GOOGLE_APPLICATION_CREDENTIALS` | For BigQuery features |

### Best Practices

1. **Never log secrets** — All logging sanitizes API keys, passwords, and tokens before output
2. **Minimal scope** — Each API key has only the permissions it needs (tier-based)
3. **Rotation** — Dynamic keys can be rotated at runtime via the admin API without restarts
4. **No .env in production** — Use actual environment variables (K8s secrets, Cloud Run secrets)
5. **Zod validation** — `env.ts` validates all required environment variables at startup, failing fast with clear error messages if any are missing

---

## Dependency Security

### Automated Scanning

- **npm audit** — Run regularly to check for known vulnerabilities
- **Dependabot** — Configured for automatic dependency update PRs
- **Lock file** — `package-lock.json` pinned to prevent supply chain attacks

### Minimal Dependencies

The project uses minimal runtime dependencies, preferring built-in Node.js APIs where possible:

- `crypto.timingSafeEqual` instead of third-party comparison libraries
- `crypto.randomUUID` instead of uuid packages
- Native `fetch` instead of Axios/node-fetch

---

## Deployment Security

### Container Security

- **Non-root user** — Dockerfile runs the application as a non-root user
- **Minimal base image** — Uses `node:22-slim` to reduce attack surface
- **No secrets in images** — All secrets are injected at runtime via environment variables
- **Read-only filesystem** — Container filesystem is read-only in production (K8s `readOnlyRootFilesystem: true`)

### Network Security

- **Internal-only ports** — Only port 8080 is exposed to the load balancer
- **No direct database access** — All database connections go through internal cluster networking
- **Egress restrictions** — Outbound traffic limited to known upstream APIs

### Kubernetes Security

```yaml
securityContext:
  runAsNonRoot: true
  readOnlyRootFilesystem: true
  allowPrivilegeEscalation: false
  capabilities:
    drop: ["ALL"]
```

See [Deployment](DEPLOYMENT.md) and [Infrastructure](INFRASTRUCTURE.md) for full deployment security configuration.