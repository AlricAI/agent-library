# Fallback Spec

> ## Purpose
Cascade fallback coordination - WHEN to try alternatives when provisioning fails.

## Responsibility
Orchestrates the fallback cascade: Clo

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Module Specification: fallback.py

## Purpose
Cascade fallback coordination - WHEN to try alternatives when provisioning fails.

## Responsibility
Orchestrates the fallback cascade: Cloud PC → Windows VM → Container, tracking failures and updating worker state.

## Public API

### Exports (`__all__`)
```python
__all__ = ["EndpointFallbackCoordinator", "AllEndpointsFailedError"]
```

### Exception: `AllEndpointsFailedError`
Raised when all endpoint types fail to provision.

This error indicates that the cascade fallback exhausted all options:
Cloud PC → Windows VM → Container, and none succeeded.

### Class: `EndpointFallbackCoordinator`

**State**:
```python
_provider_manager: EndpointProviderManager
```

**Methods**:

#### `__init__(provider_manager: EndpointProviderManager)`
Initialize fallback coordinator.

Args:
- `provider_manager`: Provider manager for provisioning operations

#### `async provision_with_fallback(worker: WorkerIdentity) -> dict[str, Any]`
Provision an endpoint with cascade fallback support.

Attempts to provision endpoints in this order:
1. Cloud PC (if cloud_pc_manager available)
2. Windows VM (if Cloud PC fails and windows_vm_manager available)
3. CLI Container (if both Cloud PC and Windows VM fail)

Updates worker.endpoint_type and worker.endpoint_id to reflect
the actually provisioned endpoint type.

Args:
- `worker`: Worker identity to provision endpoint for

Returns:
- Dictionary with:
  ```python
  {
      "endpoint_type": EndpointType,
      "endpoint_id": str,
      "success": bool,
      "details": dict  # varies by endpoint type
  }
  ```

Raises:
- `AllEndpointsFailedError`: If all endpoint types fail

#### `async _try_cloud_pc(worker: WorkerIdentity, failures: list) -> dict[str, Any] | None`
Try to provision Cloud PC endpoint.

Args:
- `worker`: Worker identity
- `failures`: List to append failure info to

Returns:
- Result dict if successful, None if failed

#### `async _try_windows_vm(worker: WorkerIdentity, failures: list) -> 

*[truncated — see source for full prompt]*