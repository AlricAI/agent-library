# TEST STAND VPN

> **Purpose:** (1) Get a VPN config file from the server (issue flow), (2) Use that config in a test stand to connect to the internet (WireGuard up → curl → verify).

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# VPN connection configuration test stand

**Purpose:** (1) Get a VPN config file from the server (issue flow), (2) Use that config in a test stand to connect to the internet (WireGuard up → curl → verify).

Validates VPN-related settings and config builder; emits **debug logs** for troubleshooting.

## Full test (get config + handshake + traffic)

From repo root, one command does both steps and **confirms handshake and traffic** using a local WG server (no real VPN node needed):

```bash
./scripts/run_vpn_test_stand_full.sh
```

- **Step 1:** Issue all 3 configs in container; write to `.tmp-vpn-test-stand/` (issued_awg.conf, issued_wg_obf.conf, issued_wg.conf, **server_private.key**).
- **Step 2:** `run_vpn_connectivity_local.sh` starts a local WG server container with that key, adds the issued client as peer, starts a client container with the plain WG config (endpoint = server container). Result: **handshake confirmed** and **curl ifconfig.me** succeeds (traffic via VPN).

If `server_private.key` is missing (old run), the script falls back to host `wg-quick` or Docker remote connectivity (handshake may fail if peer is not on the real server).

## Run (recommended: via manage.sh)

From repo root (uses admin-api container and `.env` from compose):

```bash
./manage.sh test-stand
```

To also write logs to a file inside the container (path is in container):

```bash
TEST_STAND_LOG=/tmp/vpn_debug.log ./manage.sh test-stand
```

## Run (standalone in backend)

From backend with project deps installed (e.g. `pip install -r requirements.txt` or use project venv):

```bash
cd backend
python scripts/test_stand_vpn_config.py
```

Options:

- `--log-file PATH` — also write logs to a file (e.g. `--log-file /tmp/vpn_debug.log`).
- `--no-env` — do not load `.env` from repo root (use current environment only).

Exit code: `0` if all checks pass, `1` otherwise.

## Run (pytest, with captured logs)

From backend:

```bash
cd backend
pytest tests/test_stand_vpn_connection.py -v -s

*[truncated — see source for full prompt]*