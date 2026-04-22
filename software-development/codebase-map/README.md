# Codebase Map

> Precise map of the repository structure, entry points, and responsibilities.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# VPN Suite — Codebase Map

Precise map of the repository structure, entry points, and responsibilities.

---

## 1. Root


| File / Dir           | Purpose                                                                                                                                                                                                               |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `manage.sh`          | Ops CLI: `up-core`, `up-api`, `up-monitoring`, `down-core`, `bootstrap`, `up-agent`, `migrate`, `seed*`, `check`, `verify`, `smoke-staging`, `config`, `config-validate`, `build*`, `backup-db`, `restore-db`, `node-*`, `server:verify`, `server:sync`, `server:reconcile`, `device:reissue`, `support-bundle`, `ps`, `logs`. See README.md and [docs/ops/runbook.md](ops/runbook.md). |
| `docker-compose.yml` | Services: admin-api, reverse-proxy, postgres, redis, telegram-vpn-bot; profile `monitoring`: prometheus, cadvisor, node-exporter, loki, promtail, grafana                                                             |
| `.env.example`       | Env template; copy to `.env` (single source of truth); manage.sh uses `.env` unless `ENV_FILE` set                                                                                                                    |
| `AGENTS.MD`          | Architecture, constraints, API contract, AmneziaWG/WireGuard control channel                                                                                                                                          |
| `README.md`          | Quick start, key commands, stack summary                                                                                                                                                                              |


### 1.2 Service inventory

*[truncated — see source for full prompt]*