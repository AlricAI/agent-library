# Prompt

> ## Technology Area
Containers

## Company Profile
- **Company Size**: Mid-size enterprise
- **Industry**: Financial Services / SaaS
- **Use Case**: Ro

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Scenario: AKS with NGINX Ingress Controller

## Technology Area
Containers

## Company Profile
- **Company Size**: Mid-size enterprise
- **Industry**: Financial Services / SaaS
- **Use Case**: Route external traffic to multiple microservices with SSL/TLS termination

## Scenario Description
Deploy AKS cluster with NGINX ingress controller for advanced routing capabilities. Configure ingress rules for multiple applications, implement SSL/TLS termination, and set up hostname-based routing.

## Azure Services Used
- Azure Kubernetes Service (AKS)
- Azure Container Registry (image storage)
- NGINX Ingress Controller (traffic routing)
- Azure Public IP (external access)
- Azure Key Vault (certificate storage)

## Prerequisites
- Azure subscription with Contributor role
- Azure CLI installed with kubectl and helm
- Docker installed
- A unique identifier for this scenario run

---

## Phase 1: Deployment and Validation

### Environment Setup
```bash
# Set variables
UNIQUE_ID=$(date +%Y%m%d%H%M%S)
RESOURCE_GROUP="azurehaymaker-containers-ingress-${UNIQUE_ID}-rg"
LOCATION="eastus"
AKS_CLUSTER="azurehaymaker-aks-ingress-${UNIQUE_ID}"
ACR_REGISTRY="azmkringress${UNIQUE_ID}"
VNET_NAME="azurehaymaker-vnet-${UNIQUE_ID}"
KEYVAULT="azurehaymaker-kv-${UNIQUE_ID}"
LOG_ANALYTICS="azurehaymaker-logs-${UNIQUE_ID}"

# Tags
TAGS="AzureHayMaker-managed=true Scenario=containers-aks-ingress Owner=AzureHayMaker"
```

### Deployment Steps
```bash
# Step 1: Create Resource Group
az group create \
  --name "${RESOURCE_GROUP}" \
  --location "${LOCATION}" \
  --tags ${TAGS}

# Step 2: Create Virtual Network
az network vnet create \
  --resource-group "${RESOURCE_GROUP}" \
  --name "${VNET_NAME}" \
  --address-prefix "10.0.0.0/16" \
  --subnet-name "aks-subnet" \
  --subnet-prefixes "10.0.0.0/22" \
  --tags ${TAGS}

SUBNET_ID=$(az network vnet subnet show \
  --resource-group "${RESOURCE_GROUP}" \
  --vnet-name "${VNET_NAME}" \
  --name "aks-subnet" \
  --query id -o tsv)

# Step 3: Create Azure

*[truncated — see source for full prompt]*