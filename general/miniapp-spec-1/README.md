# MINIAPP SPEC

> **Version:** 1.0  
**Audience:** Product, Design, Frontend  
**Principles:** Mobile-first, thumb-driven, one primary CTA per screen, progressive discl

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Telegram Mini App — VPN Product: Design & Architecture Spec

**Version:** 1.0  
**Audience:** Product, Design, Frontend  
**Principles:** Mobile-first, thumb-driven, one primary CTA per screen, progressive disclosure, emotional trust.

---

## 0. UX Principles (Mandatory)

- **A. Mobile-first, thumb-driven:** Primary actions in lower 60% of screen; tap targets ≥44px; no dense tables.
- **B. One primary action per screen:** 1 dominant CTA, 1–2 secondary actions max.
- **C. Progressive disclosure:** Advanced settings (e.g. billing history, security) revealed on demand.
- **D. Emotional trust:** Avoid aggressive colors; stable gradients; emphasize “Secure”, “Protected”, “Connected”; clear status (🟢/🔴).

---

## 0b. Information Architecture & Navigation

- **Main navigation:** Bottom tabs (max 5): **Home** | **Devices** | **Plan** | **Support** | **Settings**.
- **Stack (full-screen, no tabs):** Checkout, Referral, Server selection — entered from Plan/Home/Devices.
- **No nested tab bars;** one level of primary nav.

---

## 1. Complete Screen List

| Screen | Route | Primary CTA | Secondary |
|--------|--------|-------------|-----------|
| **Home** | `/` | Connect Now / Manage Connection | Get config, Change location, Add device |
| **Devices** | `/devices` | Add device | Reissue, Remove (per device) |
| **Plan** | `/plan` | Upgrade / Renew | Billing history, Payment methods |
| **Plans (catalog)** | (from Plan) | Select plan → Checkout | — |
| **Checkout** | `/plan/checkout/:planId` | Pay with Telegram | — |
| **Support** | `/support` | Start Troubleshooter | FAQ, Report problem, Contact |
| **Settings** | `/settings` | — | Language, Notifications, Security, Reset configs |
| **Server selection** | `/servers` | Apply server | — |
| **Referral** | `/referral` | Copy link / Share | — |

**Stack / full-screen (no bottom nav):** Checkout, Referral, Server selection.

---

## 2. Wireframe Descriptions

### Home
- **Header:** App title “VPN” (no badge in prod).
- **Conn

*[truncated — see source for full prompt]*