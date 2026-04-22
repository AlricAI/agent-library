# ORCHESTRATOR QUICKSTART

> **Get the orchestrator running in 5 minutes.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Orchestrator Quick Start

**Get the orchestrator running in 5 minutes.**

## Local Testing

```bash
# 1. Copy environment template
cp .env.orchestrator.example .env

# 2. Edit .env with your Azure credentials
vim .env

# 3. Run the orchestrator
./run_orchestrator.sh

# 4. Test it works
curl http://localhost:8080/
curl http://localhost:8080/api/metrics
curl http://localhost:8080/api/scenarios
```

## Docker Compose (Recommended)

```bash
# 1. Setup environment
cp .env.orchestrator.example .env
vim .env

# 2. Start services
docker-compose -f docker-compose.orchestrator.yml up -d

# 3. View logs
docker-compose -f docker-compose.orchestrator.yml logs -f

# 4. Test endpoints
./test_orchestrator.sh

# 5. Stop services
docker-compose -f docker-compose.orchestrator.yml down
```

## Deploy to Azure

```bash
# 1. Build and push image
export CONTAINER_REGISTRY="yourregistry"
az acr build \
  --registry $CONTAINER_REGISTRY \
  --image azure-haymaker-orchestrator:latest \
  --file Dockerfile.orchestrator \
  .

# 2. Create Container App
export RESOURCE_GROUP="azure-haymaker-rg"
export CONTAINER_ENV="haymaker-container-env"
export ACR_NAME="${CONTAINER_REGISTRY}.azurecr.io"

az containerapp create \
  --name haymaker-orchestrator \
  --resource-group $RESOURCE_GROUP \
  --environment $CONTAINER_ENV \
  --image $ACR_NAME/azure-haymaker-orchestrator:latest \
  --target-port 80 \
  --ingress external \
  --min-replicas 1 \
  --max-replicas 1 \
  --cpu 2 \
  --memory 4Gi \
  --registry-server $ACR_NAME \
  --registry-identity system \
  --env-vars \
    AZURE_TENANT_ID=$AZURE_TENANT_ID \
    AZURE_SUBSCRIPTION_ID=$AZURE_SUBSCRIPTION_ID \
    # ... other env vars ...

# 3. Enable managed identity and grant permissions
az containerapp identity assign \
  --name haymaker-orchestrator \
  --resource-group $RESOURCE_GROUP \
  --system-assigned

PRINCIPAL_ID=$(az containerapp identity show \
  --name haymaker-orchestrator \
  --resource-group $RESOURCE_GROUP \
  --query principalId -o ts

*[truncated — see source for full prompt]*