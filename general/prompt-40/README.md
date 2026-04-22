# Prompt

> ## Technology Area
Containers

## Company Profile
- **Company Size**: Small to mid-size startup
- **Industry**: Technology / DevOps
- **Use Case**: Ru

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Scenario: Azure Container Instances

## Technology Area
Containers

## Company Profile
- **Company Size**: Small to mid-size startup
- **Industry**: Technology / DevOps
- **Use Case**: Run containerized jobs and microservices without managing infrastructure

## Scenario Description
Deploy serverless containers using Azure Container Instances. Create container groups, manage environment variables, implement startup hooks, and configure monitoring without provisioning VMs or orchestration platforms.

## Azure Services Used
- Azure Container Instances
- Azure Container Registry (image storage)
- Azure Storage Account (volume mounting)
- Azure Log Analytics (monitoring)

## Prerequisites
- Azure subscription with Contributor role
- Azure CLI installed
- Docker installed (for building images)
- A unique identifier for this scenario run

---

## Phase 1: Deployment and Validation

### Environment Setup
```bash
# Set variables
UNIQUE_ID=$(date +%Y%m%d%H%M%S)
RESOURCE_GROUP="azurehaymaker-containers-aci-${UNIQUE_ID}-rg"
LOCATION="eastus"
ACR_REGISTRY="azmkraci${UNIQUE_ID}"
STORAGE_ACCOUNT="azmkraci${UNIQUE_ID}"
LOG_ANALYTICS="azurehaymaker-logs-${UNIQUE_ID}"
CONTAINER_GROUP="azurehaymaker-aci-${UNIQUE_ID}"

# Tags
TAGS="AzureHayMaker-managed=true Scenario=containers-aci Owner=AzureHayMaker"
```

### Deployment Steps
```bash
# Step 1: Create Resource Group
az group create \
  --name "${RESOURCE_GROUP}" \
  --location "${LOCATION}" \
  --tags ${TAGS}

# Step 2: Create Azure Container Registry
az acr create \
  --resource-group "${RESOURCE_GROUP}" \
  --name "${ACR_REGISTRY}" \
  --sku Basic \
  --admin-enabled true \
  --tags ${TAGS}

# Step 3: Build and push container image
cat > /tmp/Dockerfile <<EOF
FROM alpine:latest
RUN apk add --no-cache curl
ENTRYPOINT ["sh"]
CMD ["-c", "while true; do echo 'Container Instance running...'; sleep 30; done"]
EOF

az acr build \
  --registry "${ACR_REGISTRY}" \
  --image "aci-sample:v1" \
  --file /tmp/Dockerfile \
  /tmp/

# Step 4: Cr

*[truncated — see source for full prompt]*