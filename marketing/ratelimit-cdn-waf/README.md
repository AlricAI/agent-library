# RATELIMIT CDN WAF

> This guide provides recommendations for configuring Content Delivery Networks (CDN) and Web Application Firewalls (WAF) to complement VirtEngine's bui

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CDN and WAF Configuration Guide for DDoS Protection

This guide provides recommendations for configuring Content Delivery Networks (CDN) and Web Application Firewalls (WAF) to complement VirtEngine's built-in rate limiting and provide comprehensive DDoS protection.

## Table of Contents

1. [Overview](#overview)
2. [Cloudflare Configuration](#cloudflare-configuration)
3. [AWS CloudFront + WAF](#aws-cloudfront--waf)
4. [Azure Front Door + WAF](#azure-front-door--waf)
5. [NGINX Rate Limiting](#nginx-rate-limiting)
6. [Best Practices](#best-practices)

---

## Overview

VirtEngine provides comprehensive application-level rate limiting, but adding a CDN/WAF layer provides:

- **Network-level DDoS protection** (Layer 3/4)
- **Edge caching** to reduce load on origin servers
- **Geographic distribution** for better performance
- **SSL/TLS termination** at the edge
- **Advanced bot detection** and challenge mechanisms

### Architecture

```
Client → CDN/WAF (Edge Protection) → VirtEngine (Application Rate Limiting) → Backend
```

---

## Cloudflare Configuration

### Basic Setup

1. **Add your domain to Cloudflare**
   - Point your domain's nameservers to Cloudflare

2. **Enable DDoS Protection**
   - Go to Security → DDoS
   - Set to "High" sensitivity
   - Enable "Advanced DDoS Protection"

3. **Configure Rate Limiting Rules**

```javascript
// Cloudflare Rate Limiting Rule
{
  "expression": "(http.request.uri.path contains \"/api/\")",
  "action": "challenge",
  "characteristics": [
    "ip.src"
  ],
  "period": 10,
  "requests_per_period": 100,
  "mitigation_timeout": 600
}
```

4. **Bot Fight Mode**
   - Go to Security → Bots
   - Enable "Bot Fight Mode" or "Super Bot Fight Mode"
   - Configure challenge rules for suspicious traffic

5. **WAF Rules**

```javascript
// Block requests with suspicious patterns
(http.request.uri.query contains "sql" or
 http.request.uri.query contains "union" or
 http.request.uri.query contains "select") and
not cf.client.bot
```

### Ad

*[truncated — see source for full prompt]*