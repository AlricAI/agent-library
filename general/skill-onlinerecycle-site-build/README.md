# SKILL ONLINERECYCLE SITE BUILD

> **Version:** 1.0 — March 2026  
**Project:** OnlineRecycle.org + #ForTheKids transparency dashboard  
**Author:** Manus AI  

---

## Overview

This d

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Skill: Multi-Domain Mission-Driven Site Build on Manus

**Version:** 1.0 — March 2026  
**Project:** OnlineRecycle.org + #ForTheKids transparency dashboard  
**Author:** Manus AI  

---

## Overview

This document captures the repeatable process used to build and deploy the OnlineRecycle.org local-business landing page alongside the #ForTheKids transparency dashboard — two distinct audiences, two distinct visual identities, served from a single Manus web project via host-based routing.

The pattern is applicable to any scenario where a single codebase must serve multiple domains with different page content, branding, or audience intent.

---

## Architecture Pattern: Host-Based Domain Routing

The core technique is server-side host detection in `server/_core/vite.ts`. Both in development (Vite middleware) and production (`serveStatic`), the server reads the `x-forwarded-host` header (set by the Manus reverse proxy) and falls back to the `Host` header. When the host matches the secondary domain, a different root HTML file is served.

```ts
// In vite.ts catch-all handler
const host = req.headers['x-forwarded-host'] || req.headers['host'] || '';
const isOnlineRecycle = host.includes('onlinerecycle.org');
const rootFile = isOnlineRecycle ? 'onlinerecycle.html' : 'index.html';
res.sendFile(path.resolve(distPath, rootFile));
```

The secondary domain's HTML (`onlinerecycle.html`) lives in `client/public/` and is served as a fully static file — no React, no tRPC, no auth. This keeps it fast, indexable, and independent of the React app's build cycle.

| Domain | Root file served | Stack |
|---|---|---|
| `forthekids.manus.space` | `index.html` → React SPA | React 19 + tRPC + Manus Auth |
| `onlinerecycle.org` | `onlinerecycle.html` | Static HTML + Vanilla JS |

---

## Honesty-First Copy Protocol

Every piece of public-facing copy was reviewed against three questions before deployment:

1. **Is this true right now?** Not "will be true," not "is planned" — is it operation

*[truncated — see source for full prompt]*