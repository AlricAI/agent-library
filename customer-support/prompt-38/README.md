# Prompt

> ## Technology Area
Compute

## Company Profile
- **Company Size**: Mid-size enterprise
- **Industry**: Financial Services
- **Use Case**: Deploy a Win

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Scenario: Windows Server VM with IIS Web Server

## Technology Area
Compute

## Company Profile
- **Company Size**: Mid-size enterprise
- **Industry**: Financial Services
- **Use Case**: Deploy a Windows Server VM with IIS for hosting legacy ASP.NET web applications

## Scenario Description
Deploy a Windows Server 2019/2022 virtual machine with Internet Information Services (IIS) installed and configured. Includes basic web content deployment, performance monitoring, and Windows Update management.

## Azure Services Used
- Azure Virtual Machines (Windows Server)
- Azure Network Interfaces
- Azure Public IP Addresses
- Azure Network Security Groups
- Azure Managed Disks

## Prerequisites
- Azure subscription with Contributor role
- Azure CLI installed and configured
- RDP client available for remote desktop access (optional for validation)
- Access to create virtual machines and manage Windows servers

---

## Phase 1: Deployment and Validation

### Environment Setup
```bash
# Set variables
UNIQUE_ID=$(date +%Y%m%d%H%M%S)
RESOURCE_GROUP="azurehaymaker-compute-${UNIQUE_ID}-rg"
LOCATION="eastus"
VM_NAME="azurehaymaker-winvm-${UNIQUE_ID}"
NIC_NAME="azurehaymaker-winnic-${UNIQUE_ID}"
NSG_NAME="azurehaymaker-winnsg-${UNIQUE_ID}"
VNET_NAME="azurehaymaker-winvnet-${UNIQUE_ID}"
SUBNET_NAME="azurehaymaker-winsubnet-${UNIQUE_ID}"
PUBLIC_IP_NAME="azurehaymaker-winpip-${UNIQUE_ID}"
ADMIN_USERNAME="azureuser"

# Tags
TAGS="AzureHayMaker-managed=true Scenario=compute-windows-iis Owner=AzureHayMaker"
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
  --address-prefix 10.0.0.0/16 \
  --subnet-name "${SUBNET_NAME}" \
  --subnet-prefix 10.0.1.0/24 \
  --tags ${TAGS}

# Step 3: Create Network Security Group
az network nsg create \
  --reso

*[truncated — see source for full prompt]*