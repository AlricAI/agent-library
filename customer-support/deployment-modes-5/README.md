# DEPLOYMENT MODES

> Status: Canonical deployment and auth mode model  
Date: 2026-02-23

## 1. Purpose

Paperclip supports two runtime modes:

1. `local_trusted`
2. `auth

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Deployment Modes

Status: Canonical deployment and auth mode model  
Date: 2026-02-23

## 1. Purpose

Paperclip supports two runtime modes:

1. `local_trusted`
2. `authenticated`

`authenticated` supports two exposure policies:

1. `private`
2. `public`

This keeps one authenticated auth stack while still separating low-friction private-network defaults from internet-facing hardening requirements.

## 2. Canonical Model

| Runtime Mode | Exposure | Human auth | Primary use |
|---|---|---|---|
| `local_trusted` | n/a | No login required | Single-operator local machine workflow |
| `authenticated` | `private` | Login required | Private-network access (for example Tailscale/VPN/LAN) |
| `authenticated` | `public` | Login required | Internet-facing/cloud deployment |

## 3. Security Policy

## `local_trusted`

- loopback-only host binding
- no human login flow
- optimized for fastest local startup

## `authenticated + private`

- login required
- low-friction URL handling (`auto` base URL mode)
- private-host trust policy required

## `authenticated + public`

- login required
- explicit public URL required
- stricter deployment checks and failures in doctor

## 4. Onboarding UX Contract

Default onboarding remains interactive and flagless:

```sh
pnpm paperclipai onboard
```

Server prompt behavior:

1. ask mode, default `local_trusted`
2. option copy:
- `local_trusted`: "Easiest for local setup (no login, localhost-only)"
- `authenticated`: "Login required; use for private network or public hosting"
3. if `authenticated`, ask exposure:
- `private`: "Private network access (for example Tailscale), lower setup friction"
- `public`: "Internet-facing deployment, stricter security requirements"
4. ask explicit public URL only for `authenticated + public`

`configure --section server` follows the same interactive behavior.

## 5. Doctor UX Contract

Default doctor remains flagless:

```sh
pnpm paperclipai doctor
```

Doctor reads configured mode/exposure and applies mode-

*[truncated — see source for full prompt]*