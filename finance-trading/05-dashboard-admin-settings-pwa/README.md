# 05 Dashboard Admin Settings Pwa

> ## Context

You are working on `crypto-vision` dashboard (`apps/dashboard/`, Next.js 15). The app has existing admin, settings, auth, and PWA infrastr

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt 05 — Dashboard Admin, Settings, PWA & Polish

## Context

You are working on `crypto-vision` dashboard (`apps/dashboard/`, Next.js 15). The app has existing admin, settings, auth, and PWA infrastructure:

- `apps/dashboard/src/app/admin/` — Admin dashboard pages
- `apps/dashboard/src/app/auth/` — Authentication pages
- `apps/dashboard/src/app/settings/` — Settings pages
- `apps/dashboard/src/app/pricing/` — Pricing/premium pages
- `apps/dashboard/src/lib/admin-auth.ts` — Admin authentication
- `apps/dashboard/src/lib/premium.ts` — Premium feature management
- `apps/dashboard/src/lib/x402-payments.ts` — x402 micropayments
- `apps/dashboard/src/components/admin/` — Admin components
- `apps/dashboard/src/components/auth/` — Auth components
- `apps/dashboard/src/components/x402/` — Payment components
- PWA manifest and service worker configured

## Task

### 1. Redesign Admin Dashboard (`/admin`)

Professional admin panel with:

**Overview Dashboard:**
- API request count (today, 7d, 30d) with chart
- Active API keys count
- Revenue from x402 payments (if applicable)
- Error rate and top errors
- System health: API status, Redis status, DB status
- Top endpoints by usage

**API Key Management (`/admin/keys`):**
- Table of all API keys: name, key (masked), created, last used, requests count, rate limit, status
- Create new key form: name, rate limit tier, description
- Revoke/rotate key actions
- Usage chart per key

**User Management (placeholder):**
- User list with activity stats
- Premium status indicators

### 2. Redesign Settings Page (`/settings`)

**Appearance:**
- Theme: Dark (default, only option — remove light mode entirely)
- Accent color picker (teal, purple, blue, orange, red)
- Number format: 1,234.56 vs 1.234,56
- Compact mode toggle (denser UI)

**Currency:**
- Default currency: USD, EUR, GBP, JPY, BTC, ETH
- Keep existing `CurrencyProvider`

**Notifications:**
- Browser push notification toggle
- Alert sound toggle
- Email notifications (placeh

*[truncated — see source for full prompt]*