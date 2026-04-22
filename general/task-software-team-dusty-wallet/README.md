# TASK SOFTWARE TEAM DUSTY WALLET

> **Created:** 2026-03-16 16:57 UTC  
**Assigned to:** Spindle (CTO), Pipeline (Backend), TapTap (Android), BugCatcher (QA)  
**Priority:** HIGH  
**Sou

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# TASK: Dusty Wallet APK — Assigned to Software Team
**Created:** 2026-03-16 16:57 UTC  
**Assigned to:** Spindle (CTO), Pipeline (Backend), TapTap (Android), BugCatcher (QA)  
**Priority:** HIGH  
**Source:** Captain's request  
**Review by:** Captain upon completion

---

## Overview
Build Dusty Wallet — an Android APK for cryptocurrency consolidation across multiple chains. Simple, secure, focused on portfolio management.

---

## Team Assignment

| Role | Assignee | Responsibility |
|------|----------|----------------|
| **Project Lead** | Spindle (CTO) | Architecture, Android project setup, review |
| **Backend** | Pipeline | API endpoints, wallet sync, transaction history |
| **Android Dev** | TapTap | UI/UX, wallet functionality, APK build |
| **QA/Security** | BugCatcher | Testing, security audit, penetration testing |

---

## Requirements

### Supported Cryptocurrencies (8)
- Bitcoin (BTC)
- Ethereum (ETH)
- Solana (SOL)
- Cardano (ADA)
- Polkadot (DOT)
- Chainlink (LINK)
- Polygon (MATIC)
- Avalanche (AVAX)

### Core Features
1. **Portfolio Dashboard**
   - Balance overview (total + per asset)
   - Price charts (24h, 7d, 30d)
   - Portfolio allocation pie chart
   - P&L tracking

2. **Send/Receive**
   - QR code generation for receiving
   - QR scanner for sending
   - Address book (save frequent contacts)
   - Transaction fee estimation

3. **Transaction History**
   - Full tx history per asset
   - Filter by date/asset/type
   - Export to CSV

4. **Security**
   - 🔐 **Encrypted private key storage** (Android Keystore + AES-256)
   - 🔐 **Biometric authentication** (fingerprint/face unlock)
   - 🔐 **Backup/recovery phrase** (BIP-39 mnemonic)
   - 🔐 **PIN/password protection** (6-digit PIN + optional password)

### Technical Specs
- **Platform:** Android 8.0+ (API 26+)
- **Language:** Kotlin (preferred) or Java
- **Architecture:** MVVM or MVI
- **UI:** Jetpack Compose (preferred) or XML layouts
- **Dependencies:**
  - Room (database)
  - Retrofit/OkHtt

*[truncated — see source for full prompt]*