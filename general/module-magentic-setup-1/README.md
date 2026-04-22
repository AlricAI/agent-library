# MODULE MAGENTIC SETUP

> ## Overview

**File Location**: `/src/azure_haymaker/provisioning/magentic_ui_setup.py`

**Responsibility**: Automated installation and configuration 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Module Specification: Magentic-UI Setup Manager

## Overview

**File Location**: `/src/azure_haymaker/provisioning/magentic_ui_setup.py`

**Responsibility**: Automated installation and configuration of Magentic-UI computer use agent on provisioned Cloud PCs via PowerShell remoting.

**Status**: Agent deployment component (Phase 2)

---

## 1. Purpose & Scope

### What It Does

The MagenticUISetupManager orchestrates agent deployment on Windows 365 Cloud PCs:

- **Bootstrap**: Enable required Windows features (PSRemoting, RDP, TLS 1.2)
- **Install**: Download and execute Magentic-UI agent package
- **Configure**: Write configuration files, set environment variables
- **Verify**: Health checks and service startup validation
- **Cleanup**: Service stop and resource cleanup

### What It Does NOT Do

- Cloud PC provisioning (W365CloudPCManager)
- User identity creation (orchestrator)
- Network configuration (Cloud PC network stack)
- Service monitoring (separate agent)

---

## 2. Class Design

### MagenticUISetupManager

**Principle**: Sequential setup with fallback retry mechanisms.

#### Constructor

```python
def __init__(
    self,
    cloud_pc_credentials: PSRemotingCredentials,
    deployment_id: str,
):
    """Initialize setup manager.

    Args:
        cloud_pc_credentials: PSRemotingCredentials with:
            - hostname: Cloud PC hostname or IP
            - username: Local admin username (e.g., "cloudpc\\admin")
            - password: Admin password
            - port: WinRM port (default 5985 or 5986 for TLS)
        deployment_id: Unique ID for this deployment (for logging/tagging)

    Raises:
        ValueError: If credentials missing required fields
    """
```

#### Instance Variables

```python
self.cloud_pc_credentials: PSRemotingCredentials
self.deployment_id: str
self.ps_client: PSRemotingClient | None  # Lazy-initialized
self.logger: logging.Logger
self.setup_state: SetupState  # Tracks what's been done
```

#### Constants

```python
# Window

*[truncated — see source for full prompt]*