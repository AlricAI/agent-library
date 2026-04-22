# 19 Infra Docker K8s Cicd

> ## Context

You are working on the deployment infrastructure for crypto-vision:

- `Dockerfile` — Main API server image
- `Dockerfile.worker` — Worker

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 19 — Infrastructure: Docker, K8s & CI/CD

## Context

You are working on the deployment infrastructure for crypto-vision:

- `Dockerfile` — Main API server image
- `Dockerfile.worker` — Worker image
- `Dockerfile.train` — ML training image
- `docker-compose.yml` — Full stack (API + Redis + PostgreSQL)
- `docker-compose.ingest.yml` — Data ingestion workers
- `cloudbuild.yaml` — GCP Cloud Build CI/CD
- `cloudbuild-workers.yaml` — Worker deployment
- `infra/k8s/` — Kubernetes manifests (12 files)
- `infra/terraform/` — Terraform configs (18 files)
- `infra/setup.sh` — Infrastructure setup script
- `infra/teardown.sh` — Teardown script

## Task

### 1. Fix the Main Dockerfile

```dockerfile
# Multi-stage build for minimal production image
# Stage 1: Build
FROM node:22-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci --production=false
COPY . .
RUN npm run build

# Stage 2: Production
FROM node:22-alpine
WORKDIR /app
COPY --from=builder /app/dist ./dist
COPY --from=builder /app/node_modules ./node_modules
COPY --from=builder /app/package.json ./
COPY --from=builder /app/agents/src ./agents/src

# Security: non-root user
RUN addgroup -g 1001 -S appuser && \
    adduser -S appuser -u 1001
USER appuser

EXPOSE 8080
HEALTHCHECK --interval=30s --timeout=3s --start-period=10s \
  CMD wget -qO- http://localhost:8080/health || exit 1

CMD ["node", "dist/src/index.js"]
```

Verify this builds and runs correctly.

### 2. Fix docker-compose.yml

Ensure the compose file works for local development:
- API service: build from Dockerfile, port 8080, depends on Redis + Postgres
- Redis: redis:7-alpine, port 6379, persistence enabled
- PostgreSQL: postgres:16-alpine, port 5432, volume for data
- Health checks on all services
- Environment variables via `.env` file
- Resource limits (memory, CPU)

Add missing services:
- Dashboard: Next.js app from `apps/dashboard/`
- Workers: run data ingestion workers

### 3. Fix docker-compose.ingest.yml

Worker-specific compose

*[truncated — see source for full prompt]*