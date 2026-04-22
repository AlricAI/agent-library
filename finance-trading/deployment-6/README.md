# DEPLOYMENT

> > How to deploy Crypto Vision to various environments.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Deployment Guide

> How to deploy Crypto Vision to various environments.

## Table of Contents

1. [Quick Start (Local)](#quick-start-local)
2. [Docker Compose](#docker-compose)
3. [Google Cloud Run](#google-cloud-run)
4. [Kubernetes](#kubernetes)
5. [Self-Hosted (VPS)](#self-hosted-vps)
6. [Environment Variables](#environment-variables)
7. [CI/CD Pipeline](#cicd-pipeline)
8. [Monitoring & Health Checks](#monitoring--health-checks)
9. [Scaling](#scaling)

---

## Quick Start (Local)

```bash
# Install dependencies
npm install

# Configure environment
cp .env.example .env
# Edit .env with your API keys

# Start development server (hot reload)
npm run dev

# Or build and run production
npm run build
npm start
```

Server starts on `http://localhost:8080`.

---

## Docker Compose

The simplest production-ready deployment. No cloud dependencies.

### Full Stack (API + Redis + PostgreSQL)

```bash
# Build and start all services
docker compose up -d

# View logs
docker compose logs -f api

# Stop
docker compose down
```

**Services:**

| Service | Image | Port | Resources |
|---------|-------|------|-----------|
| `api` | Custom (Dockerfile) | 8080 | 2Gi RAM, 4 CPU |
| `redis` | redis:7-alpine | 6379 | 256MB maxmemory, LRU eviction, AOF |
| `postgres` | postgres:16-alpine | 5432 | Default |

### With Ingestion Workers

```bash
# Start full stack + ingestion pipeline
docker compose -f docker-compose.yml -f docker-compose.ingest.yml up -d
```

Adds:
- Pub/Sub emulator
- 8 ingestion workers (market, defi, news, dex, derivatives, onchain, governance, macro)
- BigQuery emulator

### Container Details

The `Dockerfile` uses a 3-stage build:

```dockerfile
# Stage 1: Dependencies (cached layer)
FROM node:22-alpine AS deps
COPY package*.json ./
RUN npm ci --omit=dev

# Stage 2: Build (TypeScript compilation)
FROM node:22-alpine AS build
COPY . .
RUN npm run build

# Stage 3: Production (minimal image)
FROM node:22-alpine AS production
COPY --from=deps /app/node_modules ./node_m

*[truncated — see source for full prompt]*