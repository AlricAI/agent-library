# Nginx Setup Complete

> **Date**: 2025-10-25
**Server**: 47.88.89.175

## ✅ What Was Configured

### 1. Frontend (dev.codeframeapp.com)
- **URL**: https://dev.codeframeapp.co

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Nginx & SSL Configuration Complete

**Date**: 2025-10-25
**Server**: 47.88.89.175

## ✅ What Was Configured

### 1. Frontend (dev.codeframeapp.com)
- **URL**: https://dev.codeframeapp.com
- **Proxies to**: localhost:14100 (Next.js)
- **SSL Certificate**: ✅ Valid until 2026-01-23
- **Auto-renewal**: ✅ Configured via certbot
- **HTTP → HTTPS redirect**: ✅ Enabled

### 2. Backend API (api.dev.codeframeapp.com)
- **URL**: https://api.dev.codeframeapp.com
- **Proxies to**: localhost:14200 (FastAPI)
- **WebSocket support**: ✅ /ws endpoint configured
- **SSL Certificate**: ✅ Valid until 2026-01-23
- **Auto-renewal**: ✅ Configured via certbot
- **HTTP → HTTPS redirect**: ✅ Enabled

## Configuration Files

### Frontend Config
**Location**: `/etc/nginx/sites-available/dev.codeframeapp.com`
```nginx
server {
    server_name dev.codeframeapp.com;

    location / {
        proxy_pass http://127.0.0.1:14100;
        # Standard proxy headers configured
    }

    listen 443 ssl; # managed by Certbot
    listen 80; # redirects to HTTPS
}
```

### Backend Config
**Location**: `/etc/nginx/sites-available/api.dev.codeframeapp.com`
```nginx
server {
    server_name api.dev.codeframeapp.com;

    location / {
        proxy_pass http://127.0.0.1:14200;
        # Standard proxy headers configured
    }

    location /ws {
        proxy_pass http://127.0.0.1:14200;
        # WebSocket headers configured
        # 7-day timeout for persistent connections
    }

    listen 443 ssl; # managed by Certbot
    listen 80; # redirects to HTTPS
}
```

## Ports in Use

- **14100**: Next.js frontend (proxied from dev.codeframeapp.com)
- **14200**: FastAPI backend (proxied from api.dev.codeframeapp.com)

**Note**: These ports are NOT in conflict with existing applications on the server:
- Port 3000: next-server (different app)
- Port 8000: python3 (different app)
- Port 8080: docker-proxy (different app)

## SSL Certificates

### Frontend Certificate
```
Certificate: /etc/letsencrypt/live/dev.codefr

*[truncated — see source for full prompt]*