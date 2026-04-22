# Prompt

> ## Technology Area
AI & ML

## Company Profile
- **Company Size**: Small to mid-size company
- **Industry**: Customer Support / SaaS
- **Use Case**: C

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Scenario: Azure Bot Service with Q&A

## Technology Area
AI & ML

## Company Profile
- **Company Size**: Small to mid-size company
- **Industry**: Customer Support / SaaS
- **Use Case**: Create intelligent chatbot that answers frequently asked questions and provides customer support escalation

## Scenario Description
Deploy Azure Bot Service with QnA Maker knowledge base integration to create an intelligent question-answering chatbot. Configure multiple channels, set up logging, and manage conversations through Azure services.

## Azure Services Used
- Azure Bot Service
- Azure QnA Maker (Cognitive Services Language Understanding)
- Azure App Service (for bot hosting)
- Azure Storage Account (for conversation logs)
- Azure Key Vault (for credentials)
- Azure Application Insights (for bot analytics)

## Prerequisites
- Azure subscription with Contributor role
- Azure CLI installed and configured
- Bot Framework SDK (optional for local testing)
- cURL or similar tool for API calls

---

## Phase 1: Deployment and Validation

### Environment Setup
```bash
# Set variables
UNIQUE_ID=$(date +%Y%m%d%H%M%S)
RESOURCE_GROUP="azurehaymaker-bot-${UNIQUE_ID}-rg"
LOCATION="eastus"
BOT_SERVICE="azurehaymaker-bot-${UNIQUE_ID}"
BOT_APP_NAME="azurehaymaker-botapp-${UNIQUE_ID}"
QNA_RESOURCE="azurehaymaker-qna-${UNIQUE_ID}"
APP_SERVICE_PLAN="azurehaymaker-asp-${UNIQUE_ID}"
STORAGE_ACCOUNT="azhmabot${UNIQUE_ID}"
KEYVAULT="azurehaymaker-kv-${UNIQUE_ID}"
INSIGHTS_NAME="azurehaymaker-insights-${UNIQUE_ID}"

# Tags
TAGS="AzureHayMaker-managed=true Scenario=ai-ml-bot-service Owner=AzureHayMaker"
```

### Deployment Steps
```bash
# Step 1: Create Resource Group
az group create \
  --name "${RESOURCE_GROUP}" \
  --location "${LOCATION}" \
  --tags ${TAGS}

# Step 2: Create Application Insights for bot monitoring
az monitor app-insights component create \
  --app "${INSIGHTS_NAME}" \
  --resource-group "${RESOURCE_GROUP}" \
  --location "${LOCATION}" \
  --kind web \
  --tags ${TAGS}

# Step

*[truncated — see source for full prompt]*