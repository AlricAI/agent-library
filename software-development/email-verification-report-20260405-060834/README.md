# Email Verification Report 20260405 060834

> **Generated:** 2026-04-05 06:08:34 UTC
**Tester:** Miles (Dark Factory AOS)
**Test Suite:** v2.0

---

## 📊 EXECUTIVE SUMMARY

| Metric | Result |
|-

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 📧 EMAIL VERIFICATION TEST REPORT
**Generated:** 2026-04-05 06:08:34 UTC
**Tester:** Miles (Dark Factory AOS)
**Test Suite:** v2.0

---

## 📊 EXECUTIVE SUMMARY

| Metric | Result |
|--------|--------|
| **Total Tests** | 20 |
| **Online Tests** | 10 |
| **Offline Tests** | 10 |
| **Online Marked Valid** | 10/10 (100.0%) |
| **Offline Caught Invalid** | 10/10 (100.0%) |
| **Average Response Time** | 82.34ms |
| **Test Accuracy** | 100.0% |

---

## ✅ ONLINE EMAIL TESTS (Expected: VALID)

| # | Email Provider | Syntax | Domain | MX | Status | Response |
|---|---------------|--------|--------|-----|--------|----------|
| 1 | Gmail - Reliable | ✅ | ✅ | ✅ | ✅ VALID | 2.9ms |
| 2 | Microsoft - Reliable | ✅ | ✅ | ✅ | ✅ VALID | 2.1ms |
| 3 | Yahoo - Legacy | ✅ | ✅ | ✅ | ✅ VALID | 3.8ms |
| 4 | ProtonMail - Secure | ✅ | ✅ | ✅ | ✅ VALID | 129.2ms |
| 5 | Apple iCloud | ✅ | ✅ | ✅ | ✅ VALID | 88.7ms |
| 6 | Zoho Mail | ✅ | ✅ | ✅ | ✅ VALID | 56.4ms |
| 7 | Yandex | ✅ | ✅ | ✅ | ✅ VALID | 534.5ms |
| 8 | Mail.ru | ✅ | ✅ | ✅ | ✅ VALID | 374.6ms |
| 9 | GMX | ✅ | ✅ | ✅ | ✅ VALID | 306.9ms |
| 10 | Fastmail | ✅ | ✅ | ✅ | ✅ VALID | 44.4ms |

### Fixes Applied to Online Tests:

- All online tests passed successfully


## ❌ OFFLINE EMAIL TESTS (Expected: INVALID)

| # | Test Case | Syntax | Domain | MX | Status | Response |
|---|-----------|--------|--------|-----|--------|----------|
| 1 | Non-existent domain | ✅ | ❌ | ❌ | ✅ INVALID | 92.8ms |
| 2 | Invalid TLD | ✅ | ❌ | ❌ | ✅ INVALID | 10.3ms |
| 3 | Missing @ | ❌ | ❌ | ❌ | ✅ INVALID | 0.0ms |
| 4 | No local part | ❌ | ❌ | ❌ | ✅ INVALID | 0.0ms |
| 5 | Spaces in address | ❌ | ❌ | ❌ | ✅ INVALID | 0.0ms |
| 6 | Double @ | ❌ | ❌ | ❌ | ✅ INVALID | 0.0ms |
| 7 | Dot at start of domain | ❌ | ❌ | ❌ | ✅ INVALID | 0.0ms |
| 8 | Double dots | ❌ | ❌ | ❌ | ✅ INVALID | 0.1ms |
| 9 | Single char TLD | ❌ | ❌ | ❌ | ✅ INVALID | 0.0ms |
| 10 | Missing dot in domain | ❌ | ❌ | ❌ | ✅ INVALID | 0.0ms |

### Fixes Applied to Offline Tests:

- **Non-exist

*[truncated — see source for full prompt]*