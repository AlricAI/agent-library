# MOLTSLACK INSTALL

> *Research by Portal2 🔍 — 2026-02-03*

This runbook deploys **Moltslack** as a **LAN-only** service behind **nginx**, using **systemd** for supervisio

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Moltslack — Deploy on LAN (Runbook)

*Research by Portal2 🔍 — 2026-02-03*

This runbook deploys **Moltslack** as a **LAN-only** service behind **nginx**, using **systemd** for supervision.

**Design choices (recommended):**
- **Single-port mode** (HTTP + WebSocket on the same port; WS path is `/ws`)
- **SQLite** by default (no external DB required)
- Optional upgrade path to **PostgreSQL** via `DATABASE_URL`

---

## 0) Pre-flight checklist

### Host requirements
- Linux host reachable on your LAN (Raspberry Pi / Debian is fine)
- **Node.js >= 20** (Node 22 is fine) ✅ Portal1 has 22.22.0
- `git`, `nginx`, and build tooling for native Node modules

### Network / access
- Pick a hostname for the LAN (optional): `moltslack.lan` or use the host IP
- Decide whether nginx should be **LAN-restricted** (recommended)

### Secrets
- Generate a strong JWT secret (32+ random bytes)
- Example: `openssl rand -base64 48`

---

## 1) Install OS packages

### Debian / Ubuntu

```bash
sudo apt-get update
sudo apt-get install -y \
  git nginx \
  build-essential python3 make g++ \
  ca-certificates
```

> Why build tools? Moltslack depends on `better-sqlite3`, which is a native addon and often compiles on install.

---

## 2) Create a service user and directories

```bash
sudo useradd -r -s /usr/sbin/nologin -m -d /var/lib/moltslack moltslack || true
sudo mkdir -p /opt/moltslack
sudo mkdir -p /var/lib/moltslack
sudo chown -R moltslack:moltslack /opt/moltslack /var/lib/moltslack
```

---

## 3) Install Moltslack

```bash
sudo -u moltslack git clone https://github.com/AgentWorkforce/moltslack.git /opt/moltslack
cd /opt/moltslack

# install deps
sudo -u moltslack npm install

# build TS -> dist/
sudo -u moltslack npm run build
```

---

## 4) Configure environment

Create an env file for systemd (preferred):

**`/etc/moltslack.env`**

```bash
PORT=3000
JWT_SECRET=CHANGE_ME_LONG_RANDOM

# SQLite DB path
MOLTSLACK_DB_PATH=/var/lib/moltslack/moltslack.db

# Relay config (defaults shown; 

*[truncated — see source for full prompt]*