# DNS CONFIGURATION

> This document provides DNS record configurations for various DNS providers.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# DNS Configuration Guide for ModPorter AI

This document provides DNS record configurations for various DNS providers.

## Domain: modporter.ai

## Required DNS Records

### A Records (Address Records)

| Type | Name | Value | TTL | Description |
|------|------|-------|-----|-------------|
| A | @ (modporter.ai) | `<PRODUCTION_SERVER_IP>` | 3600 | Main domain |
| A | www | `<PRODUCTION_SERVER_IP>` | 3600 | WWW subdomain |
| A | api | `<PRODUCTION_SERVER_IP>` | 3600 | API subdomain |
| A | grafana | `<PRODUCTION_SERVER_IP>` | 3600 | Grafana subdomain |

### MX Records (Mail Exchange)

| Type | Name | Value | Priority | TTL | Description |
|------|------|-------|----------|-----|-------------|
| MX | @ | mx1.sendgrid.net | 10 | 3600 | SendGrid primary |
| MX | @ | mx2.sendgrid.net | 20 | 3600 | SendGrid backup |

### TXT Records (Text Records)

| Type | Name | Value | TTL | Description |
|------|------|-------|-----|-------------|
| TXT | @ | `"v=spf1 include:sendgrid.net ~all"` | 3600 | SPF for email |
| TXT | modporter.ai._domainkey | `<DKIM_KEY_FROM_SENDGRID>` | 3600 | DKIM signing |
| TXT | @ | `"v=DMARC1; p=none; rua=mailto:dmarc@modporter.ai"` | 3600 | DMARC policy |

### CNAME Records (Canonical Name)

| Type | Name | Value | TTL | Description |
|------|------|-------|-----|-------------|
| CNAME | email | u12345678.ct.sendgrid.net | 3600 | SendGrid link branding |

---

## DNS Provider Specific Instructions

### Cloudflare

1. Log in to Cloudflare Dashboard
2. Select your domain (modporter.ai)
3. Go to DNS settings
4. Add records as above
5. **Important**: Disable proxy (orange cloud) for initial SSL setup
6. After SSL is working, you can enable proxy for DDoS protection

**Cloudflare-specific settings:**
- SSL/TLS Mode: Full (strict)
- Always Use HTTPS: Enabled
- HTTP Strict Transport Security (HSTS): Enabled
- Auto Minify: Enabled for HTML, CSS, JS
- Brotli Compression: Enabled

### Namecheap

1. Log in to Namecheap Dashboard
2. Select Domain List → Manage 

*[truncated — see source for full prompt]*