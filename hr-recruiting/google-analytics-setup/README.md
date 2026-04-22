# Google Analytics Setup

> ## ⏱️ Estimated Time: 10-15 minutes

This guide walks you through setting up Google Analytics credentials for the daily analytics feature. Follow each

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🔑 Google Analytics Setup Guide

## ⏱️ Estimated Time: 10-15 minutes

This guide walks you through setting up Google Analytics credentials for the daily analytics feature. Follow each step in order.

## 📋 Prerequisites

- A Google Analytics 4 (GA4) property for your website
- Access to the Google Cloud Console
- Admin access to this GitHub repository (to add secrets)

## 🔧 Step 1: Find Your GA4 Property ID

1. Open [Google Analytics](https://analytics.google.com/)
2. Select your property from the dropdown at the top left
3. Click **Admin** (gear icon at bottom left)
4. Under **Property Settings**, find your **Property ID** — it's a numeric value like `123456789`
5. Copy this number — you'll need it in Step 4

## ☁️ Step 2: Create a GCP Service Account

1. Open the [Google Cloud Console](https://console.cloud.google.com/)
2. Select or create a project — [Create a new project](https://console.cloud.google.com/projectcreate) if needed
3. Enable the **Google Analytics Data API**:
   - Go to [API Library](https://console.cloud.google.com/apis/library)
   - Search for "Google Analytics Data API"
   - Or go directly to: [Enable Google Analytics Data API](https://console.cloud.google.com/apis/library/analyticsdata.googleapis.com)
   - Click **Enable**
4. Create a service account:
   - Go to [Service Accounts](https://console.cloud.google.com/iam-admin/serviceaccounts)
   - Click **Create Service Account**
   - Name: `analytics-reader` (or any name you prefer)
   - Click **Create and Continue**
   - For role, select **Viewer** (or skip — we'll grant analytics access separately)
   - Click **Done**
5. Create a key for the service account:
   - Click on the service account you just created
   - Go to the **Keys** tab
   - Click **Add Key** → **Create new key**
   - Select **JSON** format
   - Click **Create** — a JSON file will download
   - Keep this file safe — you'll need the contents in Step 4

## 📊 Step 3: Grant Analytics Access to the Service Account

1. Open [Googl

*[truncated — see source for full prompt]*