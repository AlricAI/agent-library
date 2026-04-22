# Prompt

> ## Technology Area
Compute

## Company Profile
- **Company Size**: Small startup
- **Industry**: Data Analytics / SaaS
- **Use Case**: Deploy a Python

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Scenario: Python Web Application on Azure App Service

## Technology Area
Compute

## Company Profile
- **Company Size**: Small startup
- **Industry**: Data Analytics / SaaS
- **Use Case**: Deploy a Python Flask web application with continuous deployment and auto-scaling

## Scenario Description
Deploy a Python Flask-based web application to Azure App Service with automatic scaling, continuous integration from Git, environment configuration, and monitoring. This scenario covers serverless compute management without VM overhead.

## Azure Services Used
- Azure App Service (Web Apps)
- Azure App Service Plan
- Azure Container Registry (optional)
- Azure Application Insights
- Azure Log Analytics Workspace

## Prerequisites
- Azure subscription with Contributor role
- Azure CLI installed and configured
- Git installed locally
- Python 3.9+ installed (for local development/testing)
- A GitHub account or Git repository access (for deployment)

---

## Phase 1: Deployment and Validation

### Environment Setup
```bash
# Set variables
UNIQUE_ID=$(date +%Y%m%d%H%M%S)
RESOURCE_GROUP="azurehaymaker-compute-${UNIQUE_ID}-rg"
LOCATION="eastus"
APP_SERVICE_PLAN="azurehaymaker-asp-${UNIQUE_ID}"
WEB_APP_NAME="azurehaymaker-py-app-${UNIQUE_ID}"
APP_INSIGHTS_NAME="azurehaymaker-appinsights-${UNIQUE_ID}"
LOG_ANALYTICS_NAME="azurehaymaker-logs-${UNIQUE_ID}"
STORAGE_ACCOUNT="azurehaymaker${UNIQUE_ID}"
ARTIFACT_DIR="/tmp/azurehaymaker-flask-app"

# Tags
TAGS="AzureHayMaker-managed=true Scenario=compute-app-service-python Owner=AzureHayMaker"
```

### Deployment Steps
```bash
# Step 1: Create Resource Group
az group create \
  --name "${RESOURCE_GROUP}" \
  --location "${LOCATION}" \
  --tags ${TAGS}

# Step 2: Create Log Analytics Workspace for monitoring
az monitor log-analytics workspace create \
  --resource-group "${RESOURCE_GROUP}" \
  --workspace-name "${LOG_ANALYTICS_NAME}" \
  --location "${LOCATION}" \
  --tags ${TAGS}

LOG_ANALYTICS_ID=$(az monitor log-analytics workspace show

*[truncated — see source for full prompt]*