# API AUTHENTICATION

> > Complete guide to API key authentication, tier-based rate limiting, and key management.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# API Authentication

> Complete guide to API key authentication, tier-based rate limiting, and key management.

---

## Table of Contents

- [Overview](#overview)
- [Authentication Flow](#authentication-flow)
- [Tiers](#tiers)
- [API Key Configuration](#api-key-configuration)
  - [Static Keys](#static-keys)
  - [Dynamic Keys](#dynamic-keys)
  - [Admin Keys](#admin-keys)
- [Making Authenticated Requests](#making-authenticated-requests)
- [Rate Limit Headers](#rate-limit-headers)
- [Key Management API](#key-management-api)
- [Error Responses](#error-responses)

---

## Overview

Crypto Vision uses API key authentication with four tiers of access. Each tier provides different rate limits and feature access levels. Authentication is optional for public-tier access but required for higher rate limits and premium features.

**Source file:** `src/lib/auth.ts`

---

## Authentication Flow

```
Request arrives
     │
     ▼
Extract API key from:
  1. X-API-Key header
  2. Authorization: Bearer <key>
  3. ?api_key= query parameter
     │
     ├── No key found → assign "public" tier (30 rpm)
     │
     ├── Key found → validate:
     │     │
     │     ├── Check in-memory key store
     │     │     (seeded from API_KEYS env var)
     │     │
     │     ├── Check Redis (cv:keys:{key})
     │     │
     │     ├── Check admin keys
     │     │     (ADMIN_API_KEYS env var)
     │     │
     │     ├── Key valid → assign tier (basic/pro/enterprise)
     │     │
     │     └── Key invalid → 401 Unauthorized
     │
     ▼
Apply rate limit based on tier
     │
     ├── Within limit → proceed to route handler
     │
     └── Limit exceeded → 429 Too Many Requests
```

**Security note:** Key comparison uses `crypto.timingSafeEqual` to prevent timing side-channel attacks that could leak key values byte-by-byte.

---

## Tiers

| Tier | Rate Limit | Window | Key Required | Features |
|---|---|---|---|---|
| `public` | 30 requests | 60s | No | All read endpoints |
| `basic` | 200 requests 

*[truncated — see source for full prompt]*