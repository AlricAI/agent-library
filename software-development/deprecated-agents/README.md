# DEPRECATED AGENTS

> **Version**: 0.2.0  
**Date**: 2024-12-15  
**Updated**: 2024-12-19 (TOON format support)

---

## Overview

In v0.2.0, the legacy hardcoded agents ha

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Deprecated Agents Migration Guide

**Version**: 0.2.0  
**Date**: 2024-12-15  
**Updated**: 2024-12-19 (TOON format support)

---

## Overview

In v0.2.0, the legacy hardcoded agents have been **removed** and replaced with `ConfigurableAgent`, which is dynamically created from configuration. This provides:

- ✅ No code changes needed to modify agent behavior
- ✅ Hot-reloading of agent configurations
- ✅ Per-agent model selection
- ✅ Per-agent tool filtering
- ✅ Custom system prompts via config

### Configuration Architecture

A.R.E.S uses a **hybrid TOML + TOON** configuration system:

| Format | File | Purpose | Hot-Reload |
|--------|------|---------|------------|
| **TOML** | `ares.toml` | Infrastructure (server, auth, database, providers) | ✅ Yes |
| **TOON** | `config/*.toon` | Behavioral (agents, models, tools, workflows) | ✅ Yes |

**TOON (Token Oriented Object Notation)** is optimized for LLM consumption with 30-60% token savings.

---

## What Was Removed

The following agent files were removed in v0.2.0:

| File | Agent | Replacement |
|------|-------|-------------|
| `src/agents/product.rs` | `ProductAgent` | `ConfigurableAgent` via `config/agents/product.toon` |
| `src/agents/invoice.rs` | `InvoiceAgent` | `ConfigurableAgent` via `config/agents/invoice.toon` |
| `src/agents/sales.rs` | `SalesAgent` | `ConfigurableAgent` via `config/agents/sales.toon` |
| `src/agents/finance.rs` | `FinanceAgent` | `ConfigurableAgent` via `config/agents/finance.toon` |
| `src/agents/hr.rs` | `HrAgent` | `ConfigurableAgent` via `config/agents/hr.toon` |

---

## Migration Steps

### Step 1: Create TOON Agent Files

Create individual `.toon` files for each agent in `config/agents/`:

**config/agents/product.toon**:
```toon
name: product
model: balanced
tools[1]: calculator
system_prompt: "You are a Product Agent specialized in handling product-related queries.\n\nYour responsibilities include:\n- Providing product information and specifications\n- Helping with product reco

*[truncated — see source for full prompt]*