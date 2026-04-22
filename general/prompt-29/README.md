# Prompt

> ## Technology Area
AI & ML

## Company Profile
- **Company Size**: Enterprise
- **Industry**: Manufacturing / Predictive Analytics
- **Use Case**: Set

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Scenario: Azure Machine Learning Workspace Setup

## Technology Area
AI & ML

## Company Profile
- **Company Size**: Enterprise
- **Industry**: Manufacturing / Predictive Analytics
- **Use Case**: Set up ML workspace for training predictive models, managing experiments, and automating model deployment pipelines

## Scenario Description
Create and configure Azure Machine Learning workspace with compute resources, storage, and managed identity. Set up ML experiments, register models, and establish CI/CD integration for automated model training and deployment.

## Azure Services Used
- Azure Machine Learning Service
- Azure Storage Account (for data and models)
- Azure Cosmos DB (for experiment metadata)
- Azure Container Registry (for model containers)
- Azure Key Vault (for credentials)
- Azure Application Insights (for monitoring)

## Prerequisites
- Azure subscription with Contributor role
- Azure CLI with ML extension installed (`az extension add -n ml`)
- Python SDK for ML (optional but recommended)
- Docker (optional for custom containers)

---

## Phase 1: Deployment and Validation

### Environment Setup
```bash
# Set variables
UNIQUE_ID=$(date +%Y%m%d%H%M%S)
RESOURCE_GROUP="azurehaymaker-ml-${UNIQUE_ID}-rg"
LOCATION="eastus"
ML_WORKSPACE="azurehaymaker-ml-${UNIQUE_ID}"
STORAGE_ACCOUNT="azhmaklws${UNIQUE_ID}"
CONTAINER_REGISTRY="azhmaklcr${UNIQUE_ID}"
KEYVAULT="azurehaymaker-kv-${UNIQUE_ID}"
INSIGHTS_NAME="azurehaymaker-insights-${UNIQUE_ID}"
COMPUTE_CLUSTER="ml-cluster-${UNIQUE_ID}"

# Tags
TAGS="AzureHayMaker-managed=true Scenario=ai-ml-workspace Owner=AzureHayMaker"
```

### Deployment Steps
```bash
# Step 1: Create Resource Group
az group create \
  --name "${RESOURCE_GROUP}" \
  --location "${LOCATION}" \
  --tags ${TAGS}

# Step 2: Create Storage Account for ML workspace
az storage account create \
  --resource-group "${RESOURCE_GROUP}" \
  --name "${STORAGE_ACCOUNT}" \
  --location "${LOCATION}" \
  --sku Standard_LRS \
  --kind StorageV2 \
  --tags ${

*[truncated — see source for full prompt]*