# DEPLOYMENT

> Deploy Azure HayMaker to production

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Azure HayMaker Deployment Guide
{: .no_toc }

Complete guide for deploying Azure HayMaker infrastructure using GitOps and Azure Bicep.
{: .fs-6 .fw-300 }

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Overview

Azure HayMaker uses a fully automated GitOps deployment pipeline with:

- **Infrastructure as Code**: All Azure resources defined in Bicep templates
- **GitHub Actions**: Automated CI/CD workflows for three environments
- **OIDC Authentication**: No long-lived credentials stored in GitHub
- **Secret Management**: GitHub Secrets injected into Azure Key Vault
- **Multi-Environment**: Separate deployments for dev, staging, and production

### Architecture

```
GitHub Repository
    ├── .github/workflows/
    │   ├── deploy-containerapps.yml  (Primary: Container Apps deployment)
    │   ├── deploy-vm-orchestrator.yml (Alternative: VM deployment)
    │   └── deploy-*.yml              (Environment-specific workflows)
    │
    └── infra/bicep/
        ├── main-containerapps.bicep  (Primary: Container Apps template)
        ├── main-vm.bicep             (Alternative: VM template)
        ├── modules/                  (Reusable modules)
        └── parameters/               (Environment configs)
```

## Prerequisites

### Required Tools

1. **Azure CLI** (v2.50.0 or later)
   ```bash
   curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash
   az --version
   ```

2. **Azure Subscription** with:
   - Owner or Contributor role
   - Ability to create service principals
   - Sufficient quota for resources

3. **GitHub Repository** with:
   - Admin access
   - GitHub Actions enabled

### Required Secrets

The following secrets must be configured in your Azure subscription and GitHub repository:

| Secret Name | Description | Where to Get |
|-------------|-------------|--------------|
| AZURE_TENANT_ID | Azure AD tenant ID | Azure Portal → Azure AD → Properties |
| AZURE_SUBSCRIPTION_ID | Azure subscription ID | Azure Portal → Subscriptions |
| A

*[truncated — see source for full prompt]*