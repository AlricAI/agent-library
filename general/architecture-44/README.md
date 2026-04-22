# ARCHITECTURE

> Azure HayMaker system architecture and design

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Azure HayMaker Architecture
{: .no_toc }

System architecture and design documentation for Azure HayMaker.
{: .fs-6 .fw-300 }

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Overview

Azure HayMaker is an orchestration service that generates benign telemetry to simulate ordinary Azure tenant operations. The system executes multiple concurrent scenarios, each managed by an autonomous goal-seeking agent operating with dedicated credentials in isolated container environments.

### Core Principles

1. **Zero-BS Philosophy**: Every component implements real functionality with no stubs, TODOs, or placeholders
2. **Goal-Seeking Agents**: Autonomous agents resolve problems encountered during execution
3. **Complete Cleanup**: All resources are tracked, verified, and removed after execution
4. **Single Tenant Scope**: All operations constrained to one Azure tenant and subscription
5. **Observable Operations**: Comprehensive logging and monitoring at every level

### High-Level Architecture

```mermaid
graph TB
    subgraph "Azure Container Apps - Orchestrator (128GB RAM)"
        Timer[KEDA CRON Trigger<br/>4x Daily]
        Config[Configuration<br/>Validator]
        Selector[Scenario<br/>Selector]
        SPMgr[Service Principal<br/>Manager]
        Monitor[Monitoring<br/>Service]
        Cleanup[Cleanup<br/>Enforcer]
    end

    subgraph "Azure Container Apps - Agent Execution"
        Agent1[Agent Container 1<br/>Scenario: compute-03]
        Agent2[Agent Container 2<br/>Scenario: security-01]
        AgentN[Agent Container N<br/>Scenario: ai-ml-03]
    end

    subgraph "Azure Service Bus"
        EventBus[Event Bus<br/>Agent Logs]
    end

    subgraph "Azure Key Vault"
        Secrets[Credentials<br/>Storage]
    end

    subgraph "Target Azure Tenant"
        Resources[Deployed<br/>Resources]
    end

    Timer --> Config
    Config --> Selector
    Selector --> SPMgr
    SPMgr --> Secrets
    SPMgr --> Agent1
    SPMgr --> Agent2
    SPMgr 

*[truncated — see source for full prompt]*