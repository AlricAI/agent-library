# Configuration

> This document describes **all TOML configuration options** accepted by the OpenSandbox lifecycle server (`opensandbox-server`).

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# OpenSandbox Server configuration reference

This document describes **all TOML configuration options** accepted by the OpenSandbox lifecycle server (`opensandbox-server`). The schema is defined in [`opensandbox_server/config.py`](opensandbox_server/config.py) (`AppConfig` and nested models).

- **Default config path:** `~/.sandbox.toml`
- **Override path:** set environment variable `SANDBOX_CONFIG_PATH` to an absolute or user-expandable path.
- **CLI:** `opensandbox-server --config /path/to/sandbox.toml` also sets `SANDBOX_CONFIG_PATH` for that process.

Example files in this repository:

| File | Purpose |
|------|---------|
| [`example.config.toml`](example.config.toml) | Docker runtime (English) |
| [`example.config.zh.toml`](example.config.zh.toml) | Docker runtime (中文) |
| [`example.config.k8s.toml`](example.config.k8s.toml) | Kubernetes runtime (English) |
| [`example.config.k8s.zh.toml`](example.config.k8s.zh.toml) | Kubernetes runtime (中文) |

---

## Table of contents

1. [Top-level sections](#top-level-sections)
2. [`[server]`](#server--lifecycle-api)
3. [`[log]`](#log)
4. [`[runtime]`](#runtime--required)
5. [`[docker]`](#docker--only-when-runtime--docker)
6. [`[kubernetes]`](#kubernetes--only-when-runtime--kubernetes)
7. [`[agent_sandbox]`](#agent_sandbox--only-with-kubernetes--agent-sandbox)
8. [`[ingress]`](#ingress)
9. [`[egress]`](#egress)
10. [`[storage]`](#storage)
11. [`[secure_runtime]`](#secure_runtime)
12. [`[renew_intent]`](#renew_intent--experimental)
13. [Environment variables (outside TOML)](#environment-variables-outside-toml)
14. [Cross-field validation rules](#cross-field-validation-rules)

---

## Top-level sections

| Section | Required | When |
|---------|----------|------|
| `[server]` | No | Always (defaults apply if omitted) |
| `[log]` | No | Always (defaults apply if omitted) |
| `[runtime]` | **Yes** | Always |
| `[docker]` | No | `runtime.type = "docker"` |
| `[kubernetes]` | No | `runtime.type = "kubernetes"` (defaults are ap

*[truncated — see source for full prompt]*