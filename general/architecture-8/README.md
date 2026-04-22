# Architecture

> ## Components

```
┌─────────────────────────────────────────────────────────────┐
│                        CLI Agent                            │
│  

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# System Architecture

## Components

```
┌─────────────────────────────────────────────────────────────┐
│                        CLI Agent                            │
│  (Claude Code, Copilot CLI, Codex, etc.)                    │
│                                                             │
│  "I recommend Linear. Want me to set it up?"                │
│  → calls: agent-pay confirm linear $8/mo                    │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│                     agent-pay CLI                            │
│                                                             │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌────────────┐ │
│  │ Registry │  │ Confirmer│  │  Vault   │  │  Adapters  │ │
│  │          │  │          │  │          │  │            │ │
│  │ discover │  │ Touch ID │  │ Keychain │  │ Stripe     │ │
│  │ search   │  │ fallback │  │ pm tokens│  │ MCP        │ │
│  │ list     │  │ FIDO2    │  │ api keys │  │ (future)   │ │
│  └──────────┘  └──────────┘  └──────────┘  └────────────┘ │
└─────────────────────────┬───────────────────────────────────┘
                          │
              ┌───────────┴───────────┐
              ▼                       ▼
┌──────────────────────┐  ┌──────────────────────┐
│   macOS Keychain     │  │   Stripe API         │
│   (local storage)    │  │   (payment processing)│
│                      │  │                      │
│   - PM tokens (pm_)  │  │   - SPT creation     │
│   - API keys         │  │   - PaymentIntents   │
│   - Service creds    │  │   - Webhooks         │
└──────────────────────┘  └──────────────────────┘
```

## Component Responsibilities

### Registry

Discovers available services and their pricing. Queries the MCP registry (or a local service catalog) for:
- Service name and description
- Pricing (amount, currency, interval)
- MCP server configur

*[truncated — see source for full prompt]*