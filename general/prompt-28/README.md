# Prompt

> ## Technology Area
Analytics

## Company Profile
- **Company Size**: Mid-size retail company
- **Industry**: Retail / E-commerce
- **Use Case**: Daily

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Scenario: Scheduled Batch ETL Pipeline

## Technology Area
Analytics

## Company Profile
- **Company Size**: Mid-size retail company
- **Industry**: Retail / E-commerce
- **Use Case**: Daily sales data processing from multiple stores into a central data warehouse for business intelligence reporting

## Scenario Description
Extract daily sales data from cloud storage (CSV files uploaded by each store), transform the data to clean and aggregate it, and load it into Azure SQL Database for Power BI dashboards. The pipeline runs automatically on a daily schedule.

## Azure Services Used
- Azure Storage Account (Data Lake Gen2)
- Azure Data Factory
- Azure SQL Database
- Azure Key Vault (for connection strings)

## Prerequisites
- Azure subscription with Contributor role
- Azure CLI installed (`az --version`)
- A unique identifier for this scenario run (e.g., timestamp or GUID)

---

## Phase 1: Deployment and Validation

### Environment Setup
```bash
# Set variables
UNIQUE_ID=$(date +%Y%m%d%H%M%S)
RESOURCE_GROUP="azurehaymaker-analytics-etl-${UNIQUE_ID}-rg"
LOCATION="eastus"
STORAGE_ACCOUNT="azmkretl${UNIQUE_ID}"
SQL_SERVER="azurehaymaker-sql-${UNIQUE_ID}"
SQL_DB="saleswarehouse"
DATA_FACTORY="azurehaymaker-adf-${UNIQUE_ID}"
KEYVAULT="azurehaymaker-kv-${UNIQUE_ID}"
SQL_ADMIN_USER="sqladmin"
SQL_ADMIN_PASSWORD="P@ssw0rd!${UNIQUE_ID}"

# Tags
TAGS="AzureHayMaker-managed=true Scenario=analytics-batch-etl Owner=AzureHayMaker"
```

### Deployment Steps
```bash
# Step 1: Create Resource Group
az group create \
  --name "${RESOURCE_GROUP}" \
  --location "${LOCATION}" \
  --tags ${TAGS}

# Step 2: Create Storage Account with Data Lake Gen2
az storage account create \
  --name "${STORAGE_ACCOUNT}" \
  --resource-group "${RESOURCE_GROUP}" \
  --location "${LOCATION}" \
  --sku Standard_LRS \
  --kind StorageV2 \
  --hierarchical-namespace true \
  --tags ${TAGS}

# Step 3: Create containers for raw and processed data
STORAGE_KEY=$(az storage account keys list --resource-group "

*[truncated — see source for full prompt]*