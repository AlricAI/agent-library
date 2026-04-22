# RATELIMIT CLIENT GUIDE

> This guide helps API clients understand and work with VirtEngine's rate limiting system.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# VirtEngine Rate Limiting - Client Guide

This guide helps API clients understand and work with VirtEngine's rate limiting system.

## Table of Contents

1. [Overview](#overview)
2. [Rate Limit Headers](#rate-limit-headers)
3. [Rate Limit Tiers](#rate-limit-tiers)
4. [Handling Rate Limits](#handling-rate-limits)
5. [Best Practices](#best-practices)
6. [Code Examples](#code-examples)
7. [Troubleshooting](#troubleshooting)

---

## Overview

VirtEngine implements comprehensive rate limiting to ensure fair usage and protect against abuse. Rate limits are applied at multiple levels:

- **IP-based**: Limits per IP address
- **User-based**: Limits per authenticated user
- **Endpoint-specific**: Different limits for different endpoints
- **Global**: System-wide limits

### Why Rate Limiting?

- **Fair Access**: Ensures all users get fair access to resources
- **DDoS Protection**: Prevents denial-of-service attacks
- **Cost Control**: Reduces infrastructure costs
- **Service Quality**: Maintains performance for all users

---

## Rate Limit Headers

Every API response includes rate limit information in the headers:

```http
HTTP/1.1 200 OK
X-RateLimit-Limit: 1000
X-RateLimit-Remaining: 995
X-RateLimit-Reset: 1672531200
```

### Header Definitions

| Header | Description | Example |
|--------|-------------|---------|
| `X-RateLimit-Limit` | Maximum requests allowed in the time window | `1000` |
| `X-RateLimit-Remaining` | Number of requests remaining | `995` |
| `X-RateLimit-Reset` | Unix timestamp when the limit resets | `1672531200` |
| `Retry-After` | Seconds to wait before retrying (only on 429) | `60` |

---

## Rate Limit Tiers

### Default Limits (Per Minute)

#### Anonymous (IP-based)

```
Requests per second: 10
Requests per minute: 300
Requests per hour: 10,000
Requests per day: 100,000
Burst allowance: 20
```

#### Authenticated Users

```
Requests per second: 50
Requests per minute: 1,000
Requests per hour: 50,000
Requests per day: 500,000
Burst allowance: 100
`

*[truncated — see source for full prompt]*