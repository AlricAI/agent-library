# SCENARIO MANAGEMENT

> Azure HayMaker operational scenarios

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Scenario Management Guide
{: .no_toc }

Azure HayMaker includes 50+ operational scenarios across 10 technology areas.
{: .fs-6 .fw-300 }

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Scenario Categories

Browse scenarios by technology area:

| Category | Count | Description |
|:---------|:------|:------------|
| [AI & Machine Learning](/AzureHayMaker/scenarios/ai-ml/) | 5 | Cognitive Services, Azure OpenAI, ML Workspace |
| [Analytics](/AzureHayMaker/scenarios/analytics/) | 5 | Synapse, Databricks, Power BI |
| [Compute](/AzureHayMaker/scenarios/compute/) | 5 | VMs, App Service, Azure Functions |
| [Containers](/AzureHayMaker/scenarios/containers/) | 5 | AKS, Container Apps, Container Instances |
| [Databases](/AzureHayMaker/scenarios/databases/) | 5 | Cosmos DB, PostgreSQL, Redis |
| [Hybrid + Multicloud](/AzureHayMaker/scenarios/hybrid/) | 5 | Azure Arc, Site Recovery |
| [Identity](/AzureHayMaker/scenarios/identity/) | 5 | Entra ID, RBAC, Conditional Access |
| [Networking](/AzureHayMaker/scenarios/networking/) | 5 | VNets, Load Balancer, VPN Gateway |
| [Security](/AzureHayMaker/scenarios/security/) | 5 | Key Vault, NSGs, Security Center |
| [Web Apps](/AzureHayMaker/scenarios/webapps/) | 5 | Static Web Apps, App Service, API Management |

---

## Overview

Azure HayMaker scenarios are self-contained documentation packages that define complete operational lifecycles for Azure resources. Each scenario represents a realistic business use case executed by an autonomous agent to generate benign telemetry in an Azure tenant.

### What is a Scenario?

A scenario is a markdown document that describes:

1. **Context**: What business problem is being solved
2. **Deployment**: How to create the required Azure resources
3. **Operations**: What ongoing management activities to perform
4. **Cleanup**: How to completely remove all resources

### Scenario Lifecycle

Each scenario progresses through three phases:
1. **Phase 1 - Deployment**: Provision

*[truncated — see source for full prompt]*