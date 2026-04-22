# Single Host Network

> Detailed routing for a single-host deployment: how execd’s proxy gives every sandbox access to HTTP and WebSocket ports through one exposed host port.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Single-host network in OpenSandbox

Detailed routing for a single-host deployment: how execd’s proxy gives every sandbox access to HTTP and WebSocket ports through one exposed host port.

![Single-host sandbox routing](assets/single_host_network.png)

## Single-host routing model
- Every sandbox container starts `execd` listening on container port `44772`. `execd` bundles a lightweight reverse proxy that intercepts requests with the `/proxy/{port}` prefix and forwards them to `127.0.0.1:{port}` inside the same container.
- The Docker runtime binds only the host side of the execd proxy port (labeled `opensandbox.io/embedding-proxy-port`). Callers use `get_endpoint(..., port=X)` to receive `{public_host}:{host_proxy_port}/proxy/{X}`, and execd transparently routes the request back to the sandbox service on port `X`.
- Because the proxy preserves `Upgrade`, `Connection`, and other HTTP headers, HTTP, Server-Sent Events, and WebSocket traffic share the same mapped host port without additional configuration.
- With this setup, a single host port per sandbox suffices to reach **all** container ports. You can safely run many sandboxes on one machine without worrying about overlapping host port allocations.
- When the caller lives inside the same Docker network (e.g., another container or Kubernetes pod), use `get_endpoint(..., resolve_internal=True)` to bypass the host mapping and return the sandbox IP (e.g., `172.17.0.3:5900`) instead.
- The diagram above shows the routing path: host traffic hits the proxy port, execd rewrites the request towards the target container port, and upstream services remain isolated within the sandbox.

## Network modes

### Host network mode (single-host constraints)
- Containers share the host network stack (`network_mode=host`) so sandbox ports are directly accessible on the host.
- Because each sandbox binds its ports on the host, this mode practically limits you to one sandbox instance per host unless you reserve dedicated ports per sand

*[truncated — see source for full prompt]*