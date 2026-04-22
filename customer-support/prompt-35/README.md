# Prompt

> ## Technology Area
Compute

## Company Profile
- **Company Size**: Small startup
- **Industry**: Event-Driven Services / APIs
- **Use Case**: Deploy s

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Scenario: Serverless HTTP Triggers with Azure Functions

## Technology Area
Compute

## Company Profile
- **Company Size**: Small startup
- **Industry**: Event-Driven Services / APIs
- **Use Case**: Deploy serverless HTTP-triggered functions for lightweight API endpoints and webhooks

## Scenario Description
Deploy Azure Functions with HTTP triggers to create serverless API endpoints. Functions automatically scale based on demand, with minimal operational overhead. Includes function monitoring, logging, and integration with Application Insights.

## Azure Services Used
- Azure Functions
- Azure Storage Account (function runtime)
- Azure Application Insights
- Azure Log Analytics Workspace
- Azure Event Grid (optional for triggers)

## Prerequisites
- Azure subscription with Contributor role
- Azure CLI installed with function core tools extension
- Node.js 18+ or Python 3.9+ for local development
- Azure Functions Core Tools installed locally (optional for testing)

---

## Phase 1: Deployment and Validation

### Environment Setup
```bash
# Set variables
UNIQUE_ID=$(date +%Y%m%d%H%M%S)
RESOURCE_GROUP="azurehaymaker-compute-${UNIQUE_ID}-rg"
LOCATION="eastus"
STORAGE_ACCOUNT="azurehaymaker${UNIQUE_ID}"
FUNCTION_APP_NAME="azurehaymaker-func-${UNIQUE_ID}"
APP_INSIGHTS_NAME="azurehaymaker-appinsights-${UNIQUE_ID}"
LOG_ANALYTICS_NAME="azurehaymaker-logs-${UNIQUE_ID}"
RUNTIME="python"  # or "node" for JavaScript
RUNTIME_VERSION="3.10"

# Tags
TAGS="AzureHayMaker-managed=true Scenario=compute-azure-functions Owner=AzureHayMaker"
```

### Deployment Steps
```bash
# Step 1: Create Resource Group
az group create \
  --name "${RESOURCE_GROUP}" \
  --location "${LOCATION}" \
  --tags ${TAGS}

# Step 2: Create Log Analytics Workspace
az monitor log-analytics workspace create \
  --resource-group "${RESOURCE_GROUP}" \
  --workspace-name "${LOG_ANALYTICS_NAME}" \
  --location "${LOCATION}" \
  --tags ${TAGS}

LOG_ANALYTICS_ID=$(az monitor log-analytics workspace show \
  --resour

*[truncated — see source for full prompt]*