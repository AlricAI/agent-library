# MODULE W365 MANAGER

> ## Overview

**File Location**: `/src/azure_haymaker/provisioning/w365_manager.py`

**Responsibility**: Orchestrate Windows 365 Cloud PC provisioning 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Module Specification: W365 Cloud PC Manager

## Overview

**File Location**: `/src/azure_haymaker/provisioning/w365_manager.py`

**Responsibility**: Orchestrate Windows 365 Cloud PC provisioning via Microsoft Graph API `deviceManagement/virtualEndpoint` endpoint.

**Status**: Core provisioning component (Phase 1)

---

## 1. Purpose & Scope

### What It Does

The W365CloudPCManager encapsulates all interactions with the Windows 365 service via Microsoft Graph API beta endpoint:

- **Policy Management**: Create, retrieve, and validate provisioning policies
- **User Assignment**: Assign users to policies (triggers async provisioning)
- **Status Tracking**: Poll for provisioning completion with exponential backoff
- **Cloud PC Retrieval**: Query details of provisioned Cloud PCs
- **Lifecycle Operations**: Delete Cloud PCs and cleanup resources

### What It Does NOT Do

- User/identity creation (handled elsewhere)
- License assignment (prerequisite)
- Network configuration (handled by W365 service)
- Agent installation (separate concern)

---

## 2. Class Design

### W365CloudPCManager

**Principle**: Stateless wrapper around Graph API calls with retry logic.

#### Constructor

```python
def __init__(
    self,
    graph_client: GraphServiceClient,
    run_id: str,
):
    """Initialize manager.

    Args:
        graph_client: Authenticated GraphServiceClient with proper permissions:
            - DeviceManagementConfiguration.Read.All
            - DeviceManagementConfiguration.Write.All
            - DeviceManagementManagedDevices.Read.All
            - DeviceManagementManagedDevices.Write.All
        run_id: Unique identifier for this provisioning run (for resource tagging)

    Raises:
        ValueError: If graph_client is None
    """
```

#### Instance Variables

```python
self.graph_client: GraphServiceClient  # Authenticated client
self.run_id: str  # Run ID for resource tracking
self.logger: logging.Logger  # Logger instance
```

#### Constants

```python
# 

*[truncated — see source for full prompt]*