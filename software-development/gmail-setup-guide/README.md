# GMAIL SETUP GUIDE

> ## Overview
This guide covers the manual steps you need to complete to enable Gmail newsletter integration in Atlas. The code will handle the technica

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Gmail API Setup Guide for Atlas Block 16

## Overview
This guide covers the manual steps you need to complete to enable Gmail newsletter integration in Atlas. The code will handle the technical implementation, but you need to set up Google Cloud credentials and configure your Gmail account.

---

## 🚨 MANUAL STEPS REQUIRED (Outside of Code)

### Step 1: Google Cloud Console Setup (10-15 minutes)

1. **Go to Google Cloud Console**: https://console.cloud.google.com/
2. **Create or Select Project**:
   - Create new project: "Atlas Email Integration"
   - Or use existing project if you have one
3. **Enable Gmail API**:
   - Go to APIs & Services > Library
   - Search for "Gmail API"
   - Click "Enable"
4. **Create OAuth 2.0 Credentials**:
   - Go to APIs & Services > Credentials
   - Click "Create Credentials" > "OAuth 2.0 Client IDs"
   - Choose "Desktop Application"
   - Name: "Atlas Gmail Access"
   - Download the JSON file
5. **Set up OAuth Consent Screen**:
   - Go to APIs & Services > OAuth consent screen
   - Choose "External" (unless you have Google Workspace)
   - Fill in required fields:
     - App name: "Atlas Personal Email Integration"
     - User support email: your email
     - Developer contact: your email
   - Add your email as test user in "Test users" section

### Step 2: Gmail Account Configuration (2-3 minutes)

1. **Create "Newsletter" Label**:
   - Open Gmail in your browser
   - Go to Settings (gear icon) > Labels
   - Create new label called "Newsletter" (exactly this name)
   - Or use existing label and update `GMAIL_LABEL_NAME` in .env

2. **Label Your Newsletters**:
   - Go through your existing newsletters
   - Apply "Newsletter" label to emails you want Atlas to process
   - Set up Gmail filters to auto-label future newsletters

### Step 3: File Setup in Atlas (2-3 minutes)

1. **Place Credentials File**:
   ```bash
   # Copy downloaded OAuth JSON file to Atlas
   cp ~/Downloads/credentials.json /home/ubuntu/dev/atlas/email_download_hist

*[truncated — see source for full prompt]*