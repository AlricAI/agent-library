# Nginx Websocket Config

> **Purpose**: Configure nginx reverse proxy to support WebSocket connections for CodeFRAME real-time updates.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Nginx WebSocket Configuration Guide

**Purpose**: Configure nginx reverse proxy to support WebSocket connections for CodeFRAME real-time updates.

**Issue**: Nginx Proxy Manager's "WebSocket Support" checkbox is insufficient and does not add the required headers for WebSocket upgrade.

**Solution**: Manually add WebSocket configuration in the Advanced tab or nginx configuration file.

---

## Quick Reference

### For Nginx Proxy Manager (GUI)

1. **Open Nginx Proxy Manager** → Proxy Hosts
2. **Edit** the proxy host for `api.codeframe.home.frankbria.net`
3. **Advanced Tab** → Paste this configuration:

```nginx
# WebSocket Support - Required Headers
proxy_http_version 1.1;
proxy_set_header Upgrade $http_upgrade;
proxy_set_header Connection "upgrade";

# WebSocket Timeouts (24 hours for persistent connections)
proxy_read_timeout 86400s;
proxy_send_timeout 86400s;
proxy_connect_timeout 60s;

# Prevent buffering (critical for WebSocket)
proxy_buffering off;

# Forward client information
proxy_set_header Host $host;
proxy_set_header X-Real-IP $remote_addr;
proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
proxy_set_header X-Forwarded-Proto $scheme;
```

4. **Save** and verify

---

## Detailed Configuration

### What Each Directive Does

#### HTTP Version
```nginx
proxy_http_version 1.1;
```
**Why**: WebSocket requires HTTP/1.1. Default nginx proxy uses HTTP/1.0.
**Effect**: Enables upgrade mechanism for WebSocket handshake.

#### Upgrade Headers
```nginx
proxy_set_header Upgrade $http_upgrade;
proxy_set_header Connection "upgrade";
```
**Why**: These headers signal the protocol upgrade from HTTP → WebSocket.
**Effect**: Nginx forwards `Upgrade: websocket` header from client to backend.

**Behind the Scenes**:
- `$http_upgrade` is an nginx variable containing the `Upgrade` header value from client
- When client sends `Upgrade: websocket`, nginx forwards it to backend
- Backend responds with 101 Switching Protocols
- Nginx passes through 101 response and swit

*[truncated — see source for full prompt]*