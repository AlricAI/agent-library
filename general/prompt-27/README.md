# Prompt

> ## Technology Area
Analytics

## Company Profile
- **Company Size**: Large enterprise
- **Industry**: Retail / E-commerce
- **Use Case**: Unified anal

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Scenario: Azure Synapse Analytics Workspace for Big Data

## Technology Area
Analytics

## Company Profile
- **Company Size**: Large enterprise
- **Industry**: Retail / E-commerce
- **Use Case**: Unified analytics platform for data warehousing, big data analytics, and machine learning

## Scenario Description
Deploy Azure Synapse Analytics workspace with dedicated SQL pool, serverless SQL pool, and Spark pool for comprehensive data analytics. Process terabytes of data using either SQL or Spark, creating a unified analytics experience.

## Azure Services Used
- Azure Synapse Analytics (workspace)
- Dedicated SQL Pool (data warehouse)
- Serverless SQL Pool (on-demand querying)
- Apache Spark Pool (big data processing)
- Azure Storage Account (data lake)
- Azure Key Vault (secrets)

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
RESOURCE_GROUP="azurehaymaker-analytics-synapse-${UNIQUE_ID}-rg"
LOCATION="eastus"
SYNAPSE_WORKSPACE="azurehaymaker-synapse-${UNIQUE_ID}"
STORAGE_ACCOUNT="azmkrsynapse${UNIQUE_ID}"
SQL_POOL_NAME="sqldwpool"
SPARK_POOL_NAME="sparkpool"
KEYVAULT="azurehaymaker-kv-${UNIQUE_ID}"
SQL_ADMIN_USER="sqladmin"
SQL_ADMIN_PASSWORD="P@ssw0rd!${UNIQUE_ID}"

# Tags
TAGS="AzureHayMaker-managed=true Scenario=analytics-synapse-analytics Owner=AzureHayMaker"
```

### Deployment Steps
```bash
# Step 1: Create Resource Group
az group create \
  --name "${RESOURCE_GROUP}" \
  --location "${LOCATION}" \
  --tags ${TAGS}

# Step 2: Create Storage Account with hierarchical namespace
az storage account create \
  --name "${STORAGE_ACCOUNT}" \
  --resource-group "${RESOURCE_GROUP}" \
  --location "${LOCATION}" \
  --sku Standard_LRS \
  --kind StorageV2 \
  --hierarchical-namespace true \
  --tags ${TAGS}

# Step 3: Create file system for Synapse
STORAGE_KEY=$(az storage

*[truncated — see source for full prompt]*