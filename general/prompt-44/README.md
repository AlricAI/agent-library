# Prompt

> ## Technology Area
Analytics

## Company Profile
- **Company Size**: Mid-size SaaS company
- **Industry**: Technology / Business Intelligence
- **Use 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Scenario: Power BI Embedded Reports

## Technology Area
Analytics

## Company Profile
- **Company Size**: Mid-size SaaS company
- **Industry**: Technology / Business Intelligence
- **Use Case**: Embed Power BI reports into customer-facing applications

## Scenario Description
Deploy Power BI Embedded capacity with datasets and reports. Create service principal for programmatic access, configure capacity scaling, and demonstrate report embedding in applications.

## Azure Services Used
- Power BI Embedded (capacity)
- Power BI API
- Azure Service Principal (authentication)
- Azure Key Vault (credentials storage)

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
RESOURCE_GROUP="azurehaymaker-analytics-powerbi-${UNIQUE_ID}-rg"
LOCATION="eastus"
POWERBI_CAPACITY="azurehaymaker-pbi-${UNIQUE_ID}"
KEYVAULT="azurehaymaker-kv-${UNIQUE_ID}"
APP_NAME="azurehaymaker-powerbi-app-${UNIQUE_ID}"

# Tags
TAGS="AzureHayMaker-managed=true Scenario=analytics-power-bi-embed Owner=AzureHayMaker"
```

### Deployment Steps
```bash
# Step 1: Create Resource Group
az group create \
  --name "${RESOURCE_GROUP}" \
  --location "${LOCATION}" \
  --tags ${TAGS}

# Step 2: Create Key Vault for storing credentials
az keyvault create \
  --name "${KEYVAULT}" \
  --resource-group "${RESOURCE_GROUP}" \
  --location "${LOCATION}" \
  --tags ${TAGS}

# Step 3: Create Service Principal for Power BI access
SP_OUTPUT=$(az ad sp create-for-rbac \
  --name "${APP_NAME}" \
  --role Reader)

SP_OBJECT_ID=$(echo ${SP_OUTPUT} | jq -r '.id')
SP_CLIENT_ID=$(echo ${SP_OUTPUT} | jq -r '.appId')
SP_TENANT_ID=$(echo ${SP_OUTPUT} | jq -r '.tenant')
SP_PASSWORD=$(echo ${SP_OUTPUT} | jq -r '.password')

# Store in Key Vault
az keyvault secret set \
  --vault-name "${KEYVAULT}" \
  --name "powerbi-client-id" \
  --value "$

*[truncated — see source for full prompt]*