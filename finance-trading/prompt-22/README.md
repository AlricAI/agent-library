# Prompt

> ## Technology Area
Analytics

## Company Profile
- **Company Size**: Mid-size financial services company
- **Industry**: Financial Services / Trading


## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Scenario: Real-Time Data Streaming with Azure Stream Analytics

## Technology Area
Analytics

## Company Profile
- **Company Size**: Mid-size financial services company
- **Industry**: Financial Services / Trading
- **Use Case**: Ingest and analyze stock market data in real-time, detect anomalies, and trigger alerts

## Scenario Description
Deploy Azure Stream Analytics to process real-time data streams from Event Hubs, perform windowed aggregations, detect trading anomalies, and output results to Azure SQL Database and Power BI for live dashboarding.

## Azure Services Used
- Azure Event Hubs (data ingestion)
- Azure Stream Analytics (real-time processing)
- Azure SQL Database (results storage)
- Azure Storage (checkpoint storage)
- Azure Key Vault (connection strings)

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
RESOURCE_GROUP="azurehaymaker-analytics-streaming-${UNIQUE_ID}-rg"
LOCATION="eastus"
EVENT_HUB_NS="azurehaymaker-eh-${UNIQUE_ID}"
EVENT_HUB_NAME="stock-data-stream"
STREAM_ANALYTICS_JOB="azurehaymaker-asa-${UNIQUE_ID}"
STORAGE_ACCOUNT="azmkrstream${UNIQUE_ID}"
SQL_SERVER="azurehaymaker-sql-${UNIQUE_ID}"
SQL_DB="analyticsdb"
SQL_ADMIN_USER="sqladmin"
SQL_ADMIN_PASSWORD="P@ssw0rd!${UNIQUE_ID}"

# Tags
TAGS="AzureHayMaker-managed=true Scenario=analytics-realtime-streaming Owner=AzureHayMaker"
```

### Deployment Steps
```bash
# Step 1: Create Resource Group
az group create \
  --name "${RESOURCE_GROUP}" \
  --location "${LOCATION}" \
  --tags ${TAGS}

# Step 2: Create Storage Account for checkpoint storage
az storage account create \
  --name "${STORAGE_ACCOUNT}" \
  --resource-group "${RESOURCE_GROUP}" \
  --location "${LOCATION}" \
  --sku Standard_LRS \
  --kind StorageV2 \
  --tags ${TAGS}

STORAGE_KEY=$(az storage account keys list \
  --resource-grou

*[truncated — see source for full prompt]*