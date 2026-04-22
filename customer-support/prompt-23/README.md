# Prompt

> ## Technology Area
AI & ML

## Company Profile
- **Company Size**: Mid-size tech company
- **Industry**: Customer Service / SaaS Platform
- **Use Case

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Scenario: Text Analytics for Sentiment Analysis

## Technology Area
AI & ML

## Company Profile
- **Company Size**: Mid-size tech company
- **Industry**: Customer Service / SaaS Platform
- **Use Case**: Analyze customer feedback and support tickets for sentiment to prioritize high-value support cases and identify trends

## Scenario Description
Deploy Azure Cognitive Services Text Analytics to analyze customer feedback, support tickets, and reviews for sentiment scores and key phrases. This scenario demonstrates text processing, sentiment classification, and operational management of language AI services.

## Azure Services Used
- Azure Cognitive Services (Text Analytics)
- Azure Storage Account (for text data storage)
- Azure Cosmos DB (for storing analysis results)
- Azure Key Vault (for API credentials)

## Prerequisites
- Azure subscription with Contributor role
- Azure CLI installed and configured
- Sample text data for analysis
- cURL or similar tool for API calls

---

## Phase 1: Deployment and Validation

### Environment Setup
```bash
# Set variables
UNIQUE_ID=$(date +%Y%m%d%H%M%S)
RESOURCE_GROUP="azurehaymaker-textanalytics-${UNIQUE_ID}-rg"
LOCATION="eastus"
TEXT_RESOURCE="azurehaymaker-text-${UNIQUE_ID}"
STORAGE_ACCOUNT="azhmaktext${UNIQUE_ID}"
COSMOS_ACCOUNT="azurehaymaker-cosmos-${UNIQUE_ID}"
KEYVAULT="azurehaymaker-kv-${UNIQUE_ID}"
COSMOS_DB="sentiment-analysis"

# Tags
TAGS="AzureHayMaker-managed=true Scenario=ai-ml-text-analytics Owner=AzureHayMaker"
```

### Deployment Steps
```bash
# Step 1: Create Resource Group
az group create \
  --name "${RESOURCE_GROUP}" \
  --location "${LOCATION}" \
  --tags ${TAGS}

# Step 2: Create Azure Cognitive Services Text Analytics
az cognitiveservices account create \
  --resource-group "${RESOURCE_GROUP}" \
  --name "${TEXT_RESOURCE}" \
  --kind TextAnalytics \
  --sku S0 \
  --location "${LOCATION}" \
  --custom-domain "${TEXT_RESOURCE}" \
  --tags ${TAGS}

# Step 3: Get Text Analytics endpoint and key
TEXT_ENDP

*[truncated — see source for full prompt]*