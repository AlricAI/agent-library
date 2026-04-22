# Prompt

> ## Technology Area
Compute

## Company Profile
- **Company Size**: Mid-size enterprise
- **Industry**: E-Commerce / Retail
- **Use Case**: Deploy auto

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Scenario: Auto-Scaling VM Scale Set with Load Balancer

## Technology Area
Compute

## Company Profile
- **Company Size**: Mid-size enterprise
- **Industry**: E-Commerce / Retail
- **Use Case**: Deploy auto-scaling virtual machine fleet with load balancing for high-traffic web applications

## Scenario Description
Deploy an Azure Virtual Machine Scale Set with automatic scaling based on CPU utilization, fronted by an Azure Load Balancer for traffic distribution. Includes monitoring, scaling rules configuration, and traffic management.

## Azure Services Used
- Azure Virtual Machine Scale Sets
- Azure Load Balancer
- Azure Network Interfaces
- Azure Network Security Groups
- Azure Public IP Addresses
- Azure Monitor with auto-scaling rules

## Prerequisites
- Azure subscription with Contributor role
- Azure CLI installed and configured
- Basic understanding of load balancing concepts
- Access to create VMs and networking resources

---

## Phase 1: Deployment and Validation

### Environment Setup
```bash
# Set variables
UNIQUE_ID=$(date +%Y%m%d%H%M%S)
RESOURCE_GROUP="azurehaymaker-compute-${UNIQUE_ID}-rg"
LOCATION="eastus"
VMSS_NAME="azurehaymaker-vmss-${UNIQUE_ID}"
LB_NAME="azurehaymaker-lb-${UNIQUE_ID}"
LB_BACKEND_POOL="azurehaymaker-backend-${UNIQUE_ID}"
LB_FRONTEND_IP="azurehaymaker-frontend-${UNIQUE_ID}"
NSG_NAME="azurehaymaker-vmss-nsg-${UNIQUE_ID}"
VNET_NAME="azurehaymaker-vmss-vnet-${UNIQUE_ID}"
SUBNET_NAME="azurehaymaker-vmss-subnet-${UNIQUE_ID}"
PUBLIC_IP_NAME="azurehaymaker-lb-pip-${UNIQUE_ID}"
AUTOSCALE_NAME="azurehaymaker-autoscale-${UNIQUE_ID}"

# Tags
TAGS="AzureHayMaker-managed=true Scenario=compute-vm-scale-set Owner=AzureHayMaker"
```

### Deployment Steps
```bash
# Step 1: Create Resource Group
az group create \
  --name "${RESOURCE_GROUP}" \
  --location "${LOCATION}" \
  --tags ${TAGS}

# Step 2: Create Virtual Network and Subnet
az network vnet create \
  --resource-group "${RESOURCE_GROUP}" \
  --name "${VNET_NAME}" \
  --address-prefix 10.0.

*[truncated — see source for full prompt]*