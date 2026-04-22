# SECURITY GUIDE

> > Security architecture, threat mitigations, and best practices for the Crypto Vision platform.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Security Guide

> Security architecture, threat mitigations, and best practices for the Crypto Vision platform.

---

## Table of Contents

- [Security Architecture](#security-architecture)
- [Transport Security](#transport-security)
- [Authentication](#authentication)
- [Rate Limiting](#rate-limiting)
- [Input Validation](#input-validation)
- [Output Security](#output-security)
- [HTTP Security Headers](#http-security-headers)
- [CORS Policy](#cors-policy)
- [Secret Management](#secret-management)
- [Error Redaction](#error-redaction)
- [Dependency Security](#dependency-security)
- [Deployment Security](#deployment-security)

---

## Security Architecture

```
Client Request
     │
     ▼
┌────────────────────────────────────────────────────┐
│ Layer 1: Transport (TLS)                           │
│   • HTTPS enforced in production                   │
│   • HSTS with 1-year max-age                       │
└────────────────────┬───────────────────────────────┘
                     │
┌────────────────────▼───────────────────────────────┐
│ Layer 2: HTTP Security Headers                     │
│   • CSP, X-Frame-Options, X-Content-Type-Options   │
│   • Referrer-Policy, Permissions-Policy             │
└────────────────────┬───────────────────────────────┘
                     │
┌────────────────────▼───────────────────────────────┐
│ Layer 3: Body Size Limiting (256KB)                │
│   • Prevents memory exhaustion attacks              │
└────────────────────┬───────────────────────────────┘
                     │
┌────────────────────▼───────────────────────────────┐
│ Layer 4: CORS Validation                           │
│   • Whitelist in production, open in development    │
└────────────────────┬───────────────────────────────┘
                     │
┌────────────────────▼───────────────────────────────┐
│ Layer 5: Rate Limiting (sliding window)            │
│   • Per-IP for anonymous, per-key for authenticated │
│   • Redis backend with Lua atomic operations  

*[truncated — see source for full prompt]*