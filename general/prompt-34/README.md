# Prompt

> ## Technology Area
Analytics

## Company Profile
- **Company Size**: Large technology company
- **Industry**: Technology / SaaS
- **Use Case**: Build 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Scenario: Azure Databricks Cluster for Machine Learning

## Technology Area
Analytics

## Company Profile
- **Company Size**: Large technology company
- **Industry**: Technology / SaaS
- **Use Case**: Build and train machine learning models using Apache Spark with collaborative notebooks

## Scenario Description
Deploy Azure Databricks with an Apache Spark cluster for collaborative data science work. Create notebooks, process large datasets using Spark, and prepare data for machine learning model training.

## Azure Services Used
- Azure Databricks
- Azure Storage Account (data lake)
- Azure Key Vault (credentials)
- Azure Virtual Network (network isolation)

## Prerequisites
- Azure subscription with Contributor role
- Azure CLI installed
- A unique identifier for this scenario run

---

## Phase 1: Deployment and Validation

### Environment Setup
```bash
# Set variables
UNIQUE_ID=$(date +%Y%m%d%H%M%S)
RESOURCE_GROUP="azurehaymaker-analytics-databricks-${UNIQUE_ID}-rg"
LOCATION="eastus"
DATABRICKS_WORKSPACE="azurehaymaker-dbk-${UNIQUE_ID}"
STORAGE_ACCOUNT="azmkrdbk${UNIQUE_ID}"
KEYVAULT="azurehaymaker-kv-${UNIQUE_ID}"
VNET_NAME="azurehaymaker-vnet-${UNIQUE_ID}"

# Tags
TAGS="AzureHayMaker-managed=true Scenario=analytics-databricks Owner=AzureHayMaker"
```

### Deployment Steps
```bash
# Step 1: Create Resource Group
az group create \
  --name "${RESOURCE_GROUP}" \
  --location "${LOCATION}" \
  --tags ${TAGS}

# Step 2: Create Virtual Network for Databricks
az network vnet create \
  --resource-group "${RESOURCE_GROUP}" \
  --name "${VNET_NAME}" \
  --address-prefix "10.0.0.0/16" \
  --subnet-name "default" \
  --subnet-prefixes "10.0.0.0/24" \
  --tags ${TAGS}

# Step 3: Get VNet and subnet IDs
VNET_ID=$(az network vnet show \
  --resource-group "${RESOURCE_GROUP}" \
  --name "${VNET_NAME}" \
  --query id -o tsv)

SUBNET_ID=$(az network vnet subnet show \
  --resource-group "${RESOURCE_GROUP}" \
  --vnet-name "${VNET_NAME}" \
  --name "default" \
  --query id -o

*[truncated — see source for full prompt]*