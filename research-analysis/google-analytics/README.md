# Google Analytics

> ## 🎯 Overview

📈 Automatically fetches Google Analytics data and adds a daily statistics section to reflection notes.
🤖 Uses the GA4 Data API to re

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 📊 Google Analytics Integration

## 🎯 Overview

📈 Automatically fetches Google Analytics data and adds a daily statistics section to reflection notes.
🤖 Uses the GA4 Data API to retrieve yesterday's metrics each day at 1 AM Pacific time.
🔗 Integrates with the existing daily reflection system — no manual work required.

## 🏗️ Architecture

### 📦 Components

| 🧩 Component | 📂 Path | 📝 Purpose |
|---|---|---|
| 📚 Library | `haskell/src/Automation/GoogleAnalytics.hs` | 🔧 Pure functions for GA4 API request building, response parsing, and reflection section formatting |
| 🔐 Auth | `haskell/src/Automation/GcpAuth.hs` | 🔑 GCP service account authentication with RSA key parsing and JWT creation |
| 🧪 Tests | `haskell/test/Automation/GoogleAnalyticsTest.hs` | ✅ Tests covering formatting, section insertion, response parsing, error detection |
| 🧪 Tests | `haskell/test/Automation/GcpAuthTest.hs` | ✅ Tests covering PKCS#8 key parsing and service account JSON parsing |
| 🔌 Integration | `haskell/app/RunScheduled.hs` | 📝 `runDailyAnalytics` task runner with HTTP status checking and transparent logging |
| ⏰ Schedule | `haskell/src/Automation/Scheduler.hs` | 🕐 `DailyAnalytics` task scheduled at 01:00 PT |
| ⚙️ Workflow | `.github/workflows/scheduled.yml` | 🤖 Passes GA_PROPERTY_ID env var (GCP_SERVICE_ACCOUNT_KEY shared with other tasks) |

### 🔄 Data Flow

```
🕐 Scheduler (hour 1 PT, at-or-after)
         ↓
🔑 Check for GA_PROPERTY_ID + GCP_SERVICE_ACCOUNT_KEY
         ↓ (if available, logs ⚠️ warning if missing)
🔐 Parse service account key & obtain OAuth2 access token
         ↓ (logs service account email)
📅 Compute yesterday's date in Pacific time
📝 Check if yesterday's reflection exists and needs analytics
         ↓ (if needed)
📡 POST to GA4 Data API runReport endpoint for summary metrics
📡 POST to GA4 Data API runReport endpoint for top 5 pages
         ↓ (logs HTTP status, response size, row count)
🔍 Check for API error responses (PERMISSION_DENI

*[truncated — see source for full prompt]*