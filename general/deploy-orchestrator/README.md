# DEPLOY ORCHESTRATOR

> Simple deployment guide for the FastAPI orchestrator.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Deploy Orchestrator to Azure Container Apps

Simple deployment guide for the FastAPI orchestrator.

## Prerequisites

1. Azure CLI installed and logged in
2. Container registry created
3. Container Apps environment created
4. All required secrets in Key Vault

## Step 1: Build and Push Image

```bash
# Set variables
export RESOURCE_GROUP="azure-haymaker-rg"
export CONTAINER_REGISTRY="yourregistry"
export ACR_NAME="${CONTAINER_REGISTRY}.azurecr.io"

# Log in to ACR
az acr login --name $CONTAINER_REGISTRY

# Build and push (using ACR build for simplicity)
az acr build \
  --registry $CONTAINER_REGISTRY \
  --image azure-haymaker-orchestrator:latest \
  --file Dockerfile.orchestrator \
  .
```

## Step 2: Create Container App

```bash
# Set environment variables
export CONTAINER_ENV="haymaker-container-env"
export AZURE_TENANT_ID="your-tenant-id"
export AZURE_SUBSCRIPTION_ID="your-subscription-id"
export AZURE_CLIENT_ID="your-client-id"
export KEY_VAULT_URL="https://your-keyvault.vault.azure.net/"
export SERVICE_BUS_NAMESPACE="your-servicebus-namespace"
export CONTAINER_IMAGE="azure-haymaker-agent:latest"
export SIMULATION_SIZE="small"
export STORAGE_ACCOUNT_NAME="yourstorageaccount"
export TABLE_STORAGE_ACCOUNT_NAME="yourtablestorageaccount"
export LOG_ANALYTICS_WORKSPACE_ID="your-workspace-id"

# Create Container App
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
    AZURE_CLIENT_ID=$AZURE_CLIENT_ID \
    KEY_VAULT_URL=$KEY_VAULT_URL \
    SERVICE_BUS_NAMESPACE=$SERVICE_BUS_NAMESPACE \
    CONTAINER_REGISTRY=$ACR_NAME \
    CONTAINER_IMAGE=$CONTAINER_I

*[truncated — see source for full prompt]*