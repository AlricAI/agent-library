# ARCHITECTURE

> ## Overview

The AdvisorsFoundry/WTAF website employs a sophisticated **middleware-based routing system** that seamlessly handles multiple domains, us

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Website Architecture Documentation

## Overview

The AdvisorsFoundry/WTAF website employs a sophisticated **middleware-based routing system** that seamlessly handles multiple domains, user-generated content, and environment-specific behaviors. The architecture supports both the coaching platform (`coaches.advisorsfoundry.ai`) and the WTAF app generator (`wtaf.me`) within a single Next.js application.

## Core Architecture Principles

1. **Middleware-First Routing**: All routing decisions happen at the middleware level before reaching page components
2. **Domain-Based Separation**: Clear separation between coaching platform and WTAF while sharing infrastructure
3. **Security-First**: API routes bypassed, iframe sandboxing for user content, environment-aware protections
4. **Dynamic User Content**: User-generated WTAF apps served through secure, isolated rendering
5. **Flexible User Experience**: Customizable user landing pages and content organization

---

## Middleware Routing System

The heart of the routing system lives in `web/middleware.ts` and acts as an intelligent traffic controller.

### Key Routing Logic

```typescript
// Critical bypasses - no processing for these routes
if (pathname.startsWith('/api/') || 
    pathname.startsWith('/login') || 
    pathname.startsWith('/_next/')) {
  return NextResponse.next()
}

// Root path routing based on domain
if (pathname === '/' && isWtafDomain) {
  // wtaf.me → WTAF landing page
  return NextResponse.rewrite(new URL('/wtaf-landing', request.url))
}

// Dynamic user/app routing
// /bart → /wtaf/bart
// /bart/my-app → /wtaf/bart/my-app
const rewritePath = `/wtaf${pathname}`
return NextResponse.rewrite(new URL(rewritePath, request.url))
```

### Domain Detection

- **Production**: `wtaf.me`, `www.wtaf.me` → WTAF ecosystem
- **Development**: `localhost`, `ngrok` → Environment-aware routing with debug logging
- **Coaching Platform**: `coaches.advisorsfoundry.ai` → AdvisorsFoundry homepage

### Route Processing Order

*[truncated — see source for full prompt]*