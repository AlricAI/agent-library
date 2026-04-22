# Manager Facade Spec

> ## Purpose
Backward compatibility facade that composes the three modules and preserves the original EndpointManager API.

## Responsibility
Provides t

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Module Specification: manager.py (Facade)

## Purpose
Backward compatibility facade that composes the three modules and preserves the original EndpointManager API.

## Responsibility
Provides the original public API by delegating to lifecycle, providers, and fallback modules.

## Public API

### Exports (`__all__`)
```python
__all__ = [
    "EndpointManager",
    "ProvisioningError",
    "AllEndpointsFailedError",
]
```

### Class: `EndpointManager`

Unified endpoint management for knowledge workers.

Coordinates provisioning and management across all endpoint types
with cascade fallback support:
- Windows 365 Cloud PCs (for rich telemetry)
- Azure Windows VMs (fallback for Computer Use Agents)
- M365 CLI Containers (for cost-effective scale)

**Attributes**:
- `_lifecycle`: EndpointLifecycleManager instance
- `_providers`: EndpointProviderManager instance
- `_fallback`: EndpointFallbackCoordinator instance
- `run_id`: HayMaker run ID for this deployment

**Methods**:

#### `__init__(cloud_pc_manager=None, windows_vm_manager=None, container_manager=None, graph_client=None, config=None, run_id="")`
Initialize EndpointManager.

**IMPORTANT**: This signature MUST match the original exactly for backward compatibility.

Args:
- `cloud_pc_manager`: Pre-configured Cloud PC manager (optional)
- `windows_vm_manager`: Pre-configured Windows VM manager (optional)
- `container_manager`: Pre-configured container manager (optional)
- `graph_client`: Microsoft Graph API client (for default managers)
- `config`: Orchestrator configuration (for default managers)
- `run_id`: HayMaker run ID for resource tagging

Implementation:
```python
self.run_id = run_id
self._providers = EndpointProviderManager(
    cloud_pc_manager, windows_vm_manager, container_manager,
    graph_client, config, run_id
)
self._lifecycle = EndpointLifecycleManager(run_id)
self._fallback = EndpointFallbackCoordinator(self._providers)

# Keep references for backward compatibility properties
self.cloud_pc_manage

*[truncated — see source for full prompt]*