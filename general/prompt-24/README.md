# Prompt

> ## Technology Area
AI & ML

## Company Profile
- **Company Size**: Small startup
- **Industry**: E-commerce / Product Management
- **Use Case**: Autom

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Scenario: Computer Vision API for Image Analysis

## Technology Area
AI & ML

## Company Profile
- **Company Size**: Small startup
- **Industry**: E-commerce / Product Management
- **Use Case**: Automated product image analysis and categorization for catalog management and quality control

## Scenario Description
Deploy Azure Cognitive Services Computer Vision API to automatically analyze product images, extract object information, and generate descriptions. This scenario covers resource provisioning, image analysis operations, and management of AI service metrics and performance.

## Azure Services Used
- Azure Cognitive Services (Computer Vision)
- Azure Storage Account (for image storage)
- Azure Key Vault (for API credentials)
- Azure Application Insights (for monitoring)

## Prerequisites
- Azure subscription with Contributor role
- Azure CLI installed and configured
- Sample images for testing (or we'll create them)
- cURL or similar tool for API calls

---

## Phase 1: Deployment and Validation

### Environment Setup
```bash
# Set variables
UNIQUE_ID=$(date +%Y%m%d%H%M%S)
RESOURCE_GROUP="azurehaymaker-vision-${UNIQUE_ID}-rg"
LOCATION="eastus"
VISION_RESOURCE="azurehaymaker-vision-${UNIQUE_ID}"
STORAGE_ACCOUNT="azhmakvision${UNIQUE_ID}"
KEYVAULT="azurehaymaker-kv-${UNIQUE_ID}"
INSIGHTS_NAME="azurehaymaker-insights-${UNIQUE_ID}"

# Tags
TAGS="AzureHayMaker-managed=true Scenario=ai-ml-vision Owner=AzureHayMaker"
```

### Deployment Steps
```bash
# Step 1: Create Resource Group
az group create \
  --name "${RESOURCE_GROUP}" \
  --location "${LOCATION}" \
  --tags ${TAGS}

# Step 2: Create Azure Cognitive Services Computer Vision
az cognitiveservices account create \
  --resource-group "${RESOURCE_GROUP}" \
  --name "${VISION_RESOURCE}" \
  --kind ComputerVision \
  --sku S0 \
  --location "${LOCATION}" \
  --custom-domain "${VISION_RESOURCE}" \
  --tags ${TAGS}

# Step 3: Get Computer Vision endpoint and key
VISION_ENDPOINT=$(az cognitiveservices account show \

*[truncated — see source for full prompt]*