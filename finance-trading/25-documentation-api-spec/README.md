# 25 Documentation Api Spec

> ## Context

You are finalizing documentation for crypto-vision, a full-stack TypeScript crypto data platform. The project has:

- **200+ API endpoints

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 25 — Documentation, API Spec & Developer Experience

## Context

You are finalizing documentation for crypto-vision, a full-stack TypeScript crypto data platform. The project has:

- **200+ API endpoints** across 39 route modules
- **37 data source adapters**
- **15 background workers**
- **43 AI agent definitions**
- **6 packages** (mcp-server, binance-mcp, bnbchain-mcp, agent-runtime, pump-agent-swarm, ucai)
- **Next.js dashboard** with 55+ pages
- **Existing docs** in `docs/` (20+ files, some stale)
- **OpenAPI specs** — `openapi.yaml` (root), plus specs in apps/dashboard, apps/news, packages/sweep

Key doc files:
```
docs/
├── AGENTS.md
├── ANOMALY_DETECTION.md
├── API_AUTHENTICATION.md
├── API_REFERENCE.md
├── ARCHITECTURE.md
├── COINGECKO_RATE_LIMITING.md
├── CONFIGURATION.md
├── DATA_PIPELINE.md
├── DATA_SOURCES.md
├── DATABASE.md
├── DEPLOYMENT.md
├── DEVELOPER_WORKFLOW.md
├── INFRASTRUCTURE.md
├── ML_TRAINING.md
├── MONITORING.md
├── PACKAGES.md
├── PERFORMANCE.md
├── REPOSITORY_GUIDE.md
├── SECURITY_GUIDE.md
├── SELF_HOSTING.md
├── TELEGRAM_BOT.md
├── TESTING.md
├── TROUBLESHOOTING.md
├── WEBSOCKET.md
└── X402_PAYMENTS.md
README.md
SECURITY.md
CONTRIBUTING.md
CHANGELOG.md
```

## Task

### 1. Update `openapi.yaml` (Root API Spec)

Regenerate the complete OpenAPI 3.1 specification from the actual route handlers:

```yaml
openapi: 3.1.0
info:
  title: Crypto Vision API
  version: 2.0.0
  description: Comprehensive cryptocurrency data and intelligence API
  license:
    name: MIT
  contact:
    name: nirholas
    url: https://github.com/nirholas/crypto-vision

servers:
  - url: http://localhost:8080
    description: Development
  - url: https://api.cryptovision.dev
    description: Production

security:
  - apiKey: []

paths:
  # Generate from ALL 39 route modules:
  # src/routes/bitcoin.ts, src/routes/market.ts, src/routes/defi.ts, etc.
  # Every endpoint must have:
  #   - Summary and description
  #   - Parameters (query, path, header) with schema

*[truncated — see source for full prompt]*