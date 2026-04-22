# Architecture

> ## Executive Summary

The Azure HayMaker Orchestration Service is a production-ready system that schedules and manages the execution of benign Azure o

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Azure HayMaker Orchestration Service - Architecture Specification

## Executive Summary

The Azure HayMaker Orchestration Service is a production-ready system that schedules and manages the execution of benign Azure operational scenarios across a target tenant. The service uses Azure Durable Functions for orchestration, Azure Container Apps for isolated agent execution, and Azure Service Bus for event streaming.

This architecture prioritizes security, reliability, and observability while adhering to the Zero-BS Philosophy: every component performs real work, no stubs, no placeholders, no TODOs.

---

## System Architecture Diagram

```
┌─────────────────────────────────────────────────────────────────────────┐
│                          AZURE HAYMAKER ORCHESTRATION                    │
└─────────────────────────────────────────────────────────────────────────┘

┌──────────────────────┐
│  Timer Trigger       │  4x daily (US, Asia, ME, EU)
│  (CRON Schedule)     │
└──────────┬───────────┘
           │
           v
┌──────────────────────────────────────────────────────────────────────────┐
│                    ORCHESTRATOR (Durable Function)                        │
│                                                                           │
│  ┌─────────────────┐   ┌──────────────────┐   ┌─────────────────┐      │
│  │  1. Validation  │──>│  2. Selection    │──>│  3. Provisioning│      │
│  │  - Credentials  │   │  - Random N      │   │  - Create SPs   │      │
│  │  - Tools        │   │  - Load agents   │   │  - Assign roles │      │
│  │  - APIs         │   │  - Validate      │   │  - Setup bus    │      │
│  └─────────────────┘   └──────────────────┘   └─────────┬───────┘      │
│                                                           │              │
│  ┌─────────────────┐   ┌──────────────────┐            │              │
│  │  6. Cleanup     │<──│  5. Monitoring   │<───────────┘              │
│  │  - Verify done  │   │  - Track logs    │               

*[truncated — see source for full prompt]*