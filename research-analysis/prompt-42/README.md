# Prompt

> ## Technology Area
Databases

## Company Profile
- **Company Size**: Large enterprise
- **Industry**: Retail / E-commerce
- **Use Case**: Global-scale

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Scenario: Azure Cosmos DB with SQL API

## Technology Area
Databases

## Company Profile
- **Company Size**: Large enterprise
- **Industry**: Retail / E-commerce
- **Use Case**: Global-scale NoSQL database for customer profiles and product catalogs

## Scenario Description
Deploy Azure Cosmos DB with SQL API for globally distributed, low-latency access to document data. Configure containers, implement partitioning strategy, set up throughput scaling, and demonstrate backup capabilities.

## Azure Services Used
- Azure Cosmos DB (multi-model database)
- Azure Key Vault (connection strings)
- Azure Monitor (logging and monitoring)
- Azure Backup (disaster recovery)

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
RESOURCE_GROUP="azurehaymaker-db-cosmos-${UNIQUE_ID}-rg"
LOCATION="eastus"
COSMOS_ACCOUNT="azurehaymaker-cosmos-${UNIQUE_ID}"
COSMOS_DB="retaildb"
KEYVAULT="azurehaymaker-kv-${UNIQUE_ID}"
LOG_ANALYTICS="azurehaymaker-logs-${UNIQUE_ID}"

# Tags
TAGS="AzureHayMaker-managed=true Scenario=databases-cosmos-db Owner=AzureHayMaker"
```

### Deployment Steps
```bash
# Step 1: Create Resource Group
az group create \
  --name "${RESOURCE_GROUP}" \
  --location "${LOCATION}" \
  --tags ${TAGS}

# Step 2: Create Key Vault
az keyvault create \
  --name "${KEYVAULT}" \
  --resource-group "${RESOURCE_GROUP}" \
  --location "${LOCATION}" \
  --tags ${TAGS}

# Step 3: Create Log Analytics Workspace
az monitor log-analytics workspace create \
  --resource-group "${RESOURCE_GROUP}" \
  --workspace-name "${LOG_ANALYTICS}" \
  --location "${LOCATION}" \
  --tags ${TAGS}

# Step 4: Create Cosmos DB Account
az cosmosdb create \
  --name "${COSMOS_ACCOUNT}" \
  --resource-group "${RESOURCE_GROUP}" \
  --locations regionName="${LOCATION}" failoverPriority=0 \
  --default-consistency-l

*[truncated — see source for full prompt]*