# ORCHESTRATION ARCHITECTURE

> ## 📐 System Overview

```
┌─────────────────────────────────────────────────────────────────┐
│                       VorstersNV Platform            

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ⚙️ AGENT ORCHESTRATION ARCHITECTURE

## 📐 System Overview

```
┌─────────────────────────────────────────────────────────────────┐
│                       VorstersNV Platform                        │
├─────────────────────────────────────────────────────────────────┤
│                                                                   │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │              Event/Webhook Layer                         │   │
│  │  (Mollie, Shop, Customer Service, Home Assistant)       │   │
│  └────────────────┬─────────────────────────────────────────┘   │
│                   │                                               │
│  ┌────────────────▼─────────────────────────────────────────┐   │
│  │           FastAPI Router Layer                           │   │
│  │  (/api/orders, /api/products, /api/support)            │   │
│  │  (Validates requests, checks auth)                      │   │
│  └────────────────┬─────────────────────────────────────────┘   │
│                   │                                               │
│  ┌────────────────▼─────────────────────────────────────────┐   │
│  │      AGENT ORCHESTRATOR (Core)                          │   │
│  │  ┌────────────────────────────────────────────────────┐ │   │
│  │  │ 1. Determine workflow                             │ │   │
│  │  │ 2. Schedule agents (seq/parallel/conditional)    │ │   │
│  │  │ 3. Pass data between agents                       │ │   │
│  │  │ 4. Handle errors & retries                        │ │   │
│  │  │ 5. Collect metrics & logs                         │ │   │
│  │  └────────────────────────────────────────────────────┘ │   │
│  └────────────────┬─────────────────────────────────────────┘   │
│                   │                                               │
│  ┌────────────────┼─────────────────────────────────────────┐   │
│  │  ┌────────┐ ┌──────────┐ ┌──────────┐ ... ┌──────────┐ │   │
│  │  │Agent 1 │ │ Agent 2  │ │ Agent 3  

*[truncated — see source for full prompt]*