# FIX PLAN APPSTORE MACOS V1.8 Rejection

> **Date**: 2026-04-16  
**Submission ID**: 86491f50-6c61-44ee-beb2-6bcbe5619270  
**Review date**: April 15, 2026  
**Device**: MacBook Pro (14-inch, N

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# macOS App Store Rejection Fix Plan — v1.8

**Date**: 2026-04-16  
**Submission ID**: 86491f50-6c61-44ee-beb2-6bcbe5619270  
**Review date**: April 15, 2026  
**Device**: MacBook Pro (14-inch, Nov 2024)

---

## Issue 1: Demo Account Login (Guideline 2.1)

**Problem**: Reviewer provided credentials `demo@clipulse.app / DemoReview2026!` but the macOS app's login UI only offers OTP (email code) sign-in. There is no password field. The backend `signInWithPassword()` already works — the UI just doesn't expose it.

**Root cause**: `SettingsTab.swift` loginSection only renders OTP flow (email → 6-digit code). No password input.

**Fix**:
1. Add a password sign-in toggle/section to `SettingsTab.loginSection` — email field + password field + "Sign In" button
2. Keep OTP as the primary flow, add "Sign in with password" as secondary option
3. Reset demo account password via Supabase admin API to ensure `DemoReview2026!` works

**Files changed**:
- `CLI Pulse Bar/CLI Pulse Bar/SettingsTab.swift` — add password login UI
- Supabase admin — reset demo user password

---

## Issue 2: IAP Not Locatable (Guideline 2.1(b))

**Problem**: Reviewer cannot find In-App Purchases (CLI Pulse Pro) within the app. The current flow: Settings → "Upgrade to Pro" button → opens separate window (`openWindow(id: "subscription")`). This is not obvious. The subscription window may also fail to load StoreKit products in sandbox.

**Root cause**: IAP is behind a separate window that the reviewer may not realize opens. The button text doesn't clearly indicate it leads to IAP.

**Fix**:
1. Add inline plan comparison cards directly in the subscription section of Settings for free-tier users (showing product names, prices, and "Subscribe" buttons)
2. Keep the separate SubscriptionView window for detailed management but make IAP accessible directly from the main settings panel
3. Verify StoreKit configuration file has correct product IDs matching App Store Connect

**Files changed**:
- `CLI Pulse Bar/CLI P

*[truncated — see source for full prompt]*