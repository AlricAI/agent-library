# 2026 03 15 Stripe Requirements

> **Research Date:** 2026-03-15  
**Prepared for:** Miles  
**Status:** Actionable Intelligence

---

## Executive Summary

Stripe offers two primary pa

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Stripe Mobile Integration Requirements
**Research Date:** 2026-03-15  
**Prepared for:** Miles  
**Status:** Actionable Intelligence

---

## Executive Summary

Stripe offers two primary paths for mobile payments: **Stripe Checkout** (fastest, hosted) and **PaymentSheet SDK** (native, customizable). For fastest time-to-market, use Stripe Checkout. For full native control, use the iOS/Android SDKs with PaymentSheet.

---

## 1. What You Need to Accept Payments in a Mobile App

### Option A: Stripe Checkout (Fastest - 2/5 Complexity)
- **What it is:** Redirect users to a Stripe-hosted payment page
- **Requirements:**
  - Stripe account (free to create)
  - Backend endpoint to create Checkout Sessions
  - HTTPS success/cancel URLs
- **Mobile integration:** Open checkout URL in WebView or browser
- **Apple Pay/Google Pay:** Supported automatically (Apple Pay enabled by default, Google Pay must be enabled in Dashboard)

### Option B: Native SDK Integration (Recommended for UX)
- **iOS SDK:** `stripe-ios` (Swift/Objective-C)
- **Android SDK:** `stripe-android` (Kotlin/Java)
- **Key Components:**
  - **PaymentSheet** (prebuilt UI) - Recommended
  - **PaymentSheet FlowController** (custom UI)
  - **Apple Pay / Google Pay** buttons (separate integration)
  - **Address Element** (autofill)

### Technical Requirements (Native SDK)
| Component | iOS | Android |
|-----------|-----|---------|
| Minimum OS | iOS 13+ | API 21+ (Android 5.0) |
| Language | Swift 5.9+ / Obj-C | Kotlin 1.8+ / Java 8+ |
| Backend | Required for PaymentIntent creation | Required for PaymentIntent creation |
| Apple Pay | iOS 11.2+ | N/A |
| Google Pay | N/A | Android 5.0+ |

### Required Backend (Both Options)
- Server endpoint to create PaymentIntents or Checkout Sessions
- Stripe Secret Key (stored server-side only)
- HTTPS endpoint for webhooks (optional but recommended)

---

## 2. Fees

### Standard Pricing (No Monthly Fees)
| Transaction Type | Fee |
|-----------------|-----|
| **Domestic Cards*

*[truncated — see source for full prompt]*