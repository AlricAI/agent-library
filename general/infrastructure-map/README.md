# INFRASTRUCTURE MAP

> **Date:** 2026-02-06
**Audited by:** Infrastructure Scout Agent
**Systems:** Portal1 (Pi 5, 192.168.1.64), Portal2 (Pi 4, SSH alias `portal2`)

---

#

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Infrastructure Scout Report: Raspberry Pi 5 (Portal1) + Pi 4 (Portal2)

**Date:** 2026-02-06
**Audited by:** Infrastructure Scout Agent
**Systems:** Portal1 (Pi 5, 192.168.1.64), Portal2 (Pi 4, SSH alias `portal2`)

---

## 1. Vanilla Pi 5 State

### Operating System

| Property | Value |
|---|---|
| **OS** | Debian GNU/Linux 13 (trixie) — NOT Raspberry Pi OS Lite |
| **Kernel** | 6.12.47+rpt-rpi-2712 (aarch64, PREEMPT) |
| **Architecture** | ARM64 (aarch64) |
| **Debian version** | 13.2 |
| **Python** | 3.13.5 (system) |
| **Node.js** | 22.22.0 (nodesource) |

> **Note:** This is Debian trixie (testing/stable), not the standard Raspberry Pi OS. It uses the RPi kernel but the Debian userland. This is more bleeding-edge than a typical Pi setup.

### Pre-installed Tools

**Available (verified `which`):**
| Tool | Path | Notes |
|---|---|---|
| bash | /usr/bin/bash | Default shell |
| python3 | /usr/bin/python3 | 3.13.5 — very recent |
| python | /usr/bin/python | Symlink to python3 |
| pip3/pip | /usr/bin/pip3 | 25.1.1 |
| apt/apt-get | /usr/bin/apt | Package manager |
| dpkg | /usr/bin/dpkg | Low-level package tool |
| systemctl | /usr/bin/systemctl | Service management |
| journalctl | /usr/bin/journalctl | Log viewer |
| ssh/scp | /usr/bin/ssh | OpenSSH 10.0p1 |
| rsync | /usr/bin/rsync | File sync |
| curl | /usr/bin/curl | 8.14.1 |
| wget | /usr/bin/wget | Downloader |
| git | /usr/bin/git | 2.47.3 |
| nano | /usr/bin/nano | Text editor |
| tmux | /usr/bin/tmux | Terminal multiplexer |
| htop | /usr/bin/htop | Process viewer |
| node | (via nodesource) | 22.22.0 |
| npm | (via nodesource) | Global packages installed |
| build-essential | installed | gcc 14.2.0, make 4.4.1, cmake 3.31.6 |

**NOT available:**
vim, screen, docker, nginx, caddy, ufw, yarn, bun, cargo, rustc, go

### Default User Setup

| Property | Value |
|---|---|
| **User** | `dcarmitage` (uid=1000, gid=1000) |
| **Groups** | adm, dialout, cdrom, **sudo**, audio, video, plugdev, games, users, in

*[truncated — see source for full prompt]*