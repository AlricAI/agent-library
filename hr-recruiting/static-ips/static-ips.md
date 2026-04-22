---
name: Static Ips
description: Outbound traffic from the New-U Peptides production infrastructure exits AWS
through a fixed set of static IPs in three regions. Share this list with 
model: claude-sonnet-4-5
---
# Static Egress IPs

Outbound traffic from the New-U Peptides production infrastructure exits AWS
through a fixed set of static IPs in three regions. Share this list with any
upstream partner (payment gateway, webhook endpoint, API provider, banking
partner, etc.) that requires IP allowlisting.

All IPs are **IPv4** and are owned/assigned to our AWS accounts — they do not
rotate.

## Regions

### London, United Kingdom — `eu-west-2`

```
35.179.191.66
18.168.208.49
```

### Washington, D.C., USA — `us-east-1`

```
34.236.169.52
52.205.167.85
```

### Frankfurt, Germany — `eu-central-1`

```
51.102.64.254
35.158.26.225
```

## Flat list (for copy/paste into allowlists)

```
35.179.191.66
18.168.208.49
34.236.169.52
52.205.167.85
51.102.64.254
35.158.26.225
```

## CIDR notation

```
35.179.191.66/32
18.168.208.49/32
34.236.169.52/32
52.205.167.85/32
51.102.64.254/32
35.158.26.225/32
```

## Notes

- These are **egress** IPs for outbound calls we make to third-party APIs. They
  are not the inbound/public-facing addresses of `new-u.io` (which is served
  through Vercel's edge network).
- If a partner asks for "the IP our requests come from", these are the values
  to provide.
- When adding or changing an IP, update this file in the same PR as the
  infrastructure change so the source of truth stays in sync.