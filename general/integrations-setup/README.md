# INTEGRATIONS SETUP

> This document provides detailed instructions for setting up each cloud integration for the Instagram extractor.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Cloud Integration Setup Guide

This document provides detailed instructions for setting up each cloud integration for the Instagram extractor.

---

## Overview

The system supports 5 cloud integrations:

1. **Google Sheets** - Export analysis results to Google Sheets
2. **BigQuery** - Store analysis data in BigQuery for analytics
3. **HubSpot** - Sync leads to HubSpot CRM
4. **Mailchimp** - Add contacts to Mailchimp audiences
5. **Salesforce** - Create accounts and contacts in Salesforce

---

## 1. Google Sheets Integration

### Setup Steps

1. **Create a Google Cloud Project**
   - Go to [Google Cloud Console](https://console.cloud.google.com)
   - Create a new project
   - Enable the Google Sheets API

2. **Create a Service Account**
   - In Google Cloud Console, go to "Service Accounts"
   - Create a new service account
   - Download the JSON key file (this is your `GOOGLE_CLOUD_CREDENTIALS`)

3. **Create a Spreadsheet**
   - Create a new Google Sheet
   - Copy the spreadsheet ID from the URL (format: `/spreadsheets/d/{SPREADSHEET_ID}/edit`)
   - Share the sheet with the service account email

4. **Set Environment Variables**
   ```bash
   GOOGLE_CLOUD_PROJECT=your-project-id
   GOOGLE_CLOUD_CREDENTIALS='{"type":"service_account",...}'
   DEFAULT_SPREADSHEET_ID=your-spreadsheet-id
   ```

### Configuration

```typescript
const credentials = {
  google_sheets: {
    spreadsheetId: 'your-spreadsheet-id',
    sheetName: 'Instagram Leads' // Optional, defaults to 'Instagram Leads'
  }
}
```

### What Gets Exported

- Extracted Date
- Username
- Company Name
- Industry
- Website
- Email
- Phone
- Instagram Handle
- Followers
- Business Type
- Services
- Target Market
- Lead Score

---

## 2. BigQuery Integration

### Setup Steps

1. **Enable BigQuery API**
   - In Google Cloud Console, enable the BigQuery API
   - Use the same Google Cloud project as Sheets (if desired)

2. **Create Dataset**
   - In BigQuery, create a new dataset (e.g., `instagram_analysis`)
   -

*[truncated — see source for full prompt]*