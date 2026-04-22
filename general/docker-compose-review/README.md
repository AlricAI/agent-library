# DOCKER COMPOSE REVIEW

> ## Summary

| File | Role | Notes |
|------|------|------|
| `docker-compose.yml` | Main stack (control-plane + monitoring profile) | Single source of

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Docker Compose files — review and optimizations

## Summary

| File | Role | Notes |
|------|------|------|
| `docker-compose.yml` | Main stack (control-plane + monitoring profile) | Single source of anchors; good security/resource defaults. |
| `docker-compose.audit.yml` | Standalone audit stack (different ports) | Self-contained; some drift from main (redis auth, prometheus/grafana config). |
| `docker-compose.observability.yml` | Merge overlay (observability extras) | Extends main; adds discovery, Tempo, VictoriaMetrics, OTEL, archive jobs. |
| `docker-compose.verification.yml` | Merge overlay (local verification) | Only overrides `admin-api` ports to `8000:8000`. |

---

## Findings and optimizations applied

### 1. docker-compose.yml

- **Alertmanager**: Replaced `image: prom/alertmanager:latest` with pinned digest for reproducible builds.
- **Other**: Anchors, healthchecks, `depends_on` conditions, and network separation (app vs db) are in good shape.

### 2. docker-compose.audit.yml

- **Standalone design**: Intentionally duplicates anchors and services (separate network `vpn-suite`, different ports). No change to that.
- **Redis**: Added `REDIS_PASSWORD` and command/healthcheck support so audit stack matches main when password is set.
- **Prometheus**: Added `recording_rules.yml` and `--storage.tsdb.path` / `--storage.tsdb.retention.time` so behavior aligns with main.
- **Grafana**: Added provisioning and dashboards volumes so dashboards work like main.
- **resource_small**: Kept at 128m for audit (main uses 256m); adjust via env if needed.
- **Unused anchor**: `x-secure-default-no-opt` is unused; can be removed in a cleanup pass.

### 3. docker-compose.observability.yml

- **VictoriaMetrics**: Replaced `latest` with a pinned version for reproducibility.
- **Merge behavior**: Correctly overlays main; networks/volumes from main are used. Archive scripts exist under `scripts/`.

### 4. docker-compose.verification.yml

- No code changes. Use with main for loc

*[truncated — see source for full prompt]*