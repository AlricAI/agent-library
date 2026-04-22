# INFRASTRUCTURE

> > Deployment, CI/CD, and infrastructure configuration for Crypto Vision.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Infrastructure

> Deployment, CI/CD, and infrastructure configuration for Crypto Vision.

## Deployment Options

| Method | Complexity | Monthly Cost | Best For |
|---|---|---|---|
| Docker Compose | Low | ~$43 (Hetzner) | Development, small deployments |
| Kubernetes | Medium | ~$50–150 | Production self-hosted |
| GCP Cloud Run | Low | ~$305 | Production managed |
| Bare metal | High | Varies | Maximum control |

---

## Docker Compose

### Full Stack

```bash
docker compose up -d
```

**Services:**

| Service | Image | Port | Description |
|---|---|---|---|
| `api` | Dockerfile (build) | 8080 | Hono API server (2G RAM, 4 CPU) |
| `redis` | redis:7-alpine | 6379 | Cache (256MB, allkeys-lru) |
| `postgres` | postgres:16-alpine | 5432 | Bot database (user: cryptovision, db: cryptovision) |
| `scheduler` | alpine (cron) | — | Periodic data refresh |

**Scheduler jobs:**
- Coins: every 2 min
- Trending/global/news: every 5 min
- Fear & Greed: every 15 min
- DeFi protocols: every 10 min

### Ingestion Workers

```bash
docker compose -f docker-compose.ingest.yml up -d
```

**Services:**

| Service | Frequency | Description |
|---|---|---|
| `pubsub-emulator` | — | GCP Pub/Sub emulator (port 8085) |
| `worker-market` | 2 min | Market data ingestion |
| `worker-defi` | 5 min | DeFi protocol data |
| `worker-news` | 5 min | News aggregation |
| `worker-dex` | 2 min | DEX pair data |
| `worker-derivatives` | 10 min | Derivatives/perps data |
| `worker-onchain` | 5 min | On-chain metrics |
| `worker-governance` | 30 min | Governance proposals |
| `worker-macro` | 60 min | Macro economic data |

### Dockerfiles

| File | Base | Purpose |
|---|---|---|
| `Dockerfile` | node:22-alpine | API server (3-stage: deps→build→run) |
| `Dockerfile.worker` | node:22-alpine | Ingestion workers (STOPSIGNAL SIGTERM) |
| `Dockerfile.train` | nvidia/cuda:12.4.0 | ML training (Python 3.11, PyTorch 2.4, Unsloth, vLLM) |

---

## Kubernetes

Manifests in `infra/k8s/` use Kustomize. Compatible 

*[truncated — see source for full prompt]*