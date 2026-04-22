# DEPLOYMENT

> ## Overview
This system enables automated issue tracking, reformulation, fixing, and PR creation for the WEBTOYS platform.

## Architecture Components

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# WEBTOYS Issue Tracker Agent - Deployment Guide

## Overview
This system enables automated issue tracking, reformulation, fixing, and PR creation for the WEBTOYS platform.

## Architecture Components

1. **Public ZAD App** (`issue-tracker-zad-app.html`)
   - Public-facing issue submission form
   - Stores issues in `wtaf_zero_admin_collaborative` table
   - Available at: `webtoys.me/[user]/issue-tracker`

2. **Reformulation Agent** (`reformulate-issues.js`)
   - Reads raw user submissions
   - Uses Claude to reformulate into actionable tickets
   - Categorizes and assigns confidence levels

3. **Auto-Fix Agent** (`fix-issues.js`)
   - Processes high-confidence issues
   - Creates feature branches
   - Implements fixes using Claude Code
   - Runs tests to verify changes

4. **PR Creation Agent** (`create-prs.js`)
   - Creates GitHub pull requests
   - Adds appropriate labels
   - Links back to original issue

5. **Monitor** (`monitor.js`)
   - Orchestrates the entire pipeline
   - Can run individual agents or full pipeline

## Deployment Steps

### 1. Deploy the ZAD App

Option A: Create new app via SMS:
```
Text to WEBTOYS: "Create an issue tracker app using the HTML from agent-issue-tracker/issue-tracker-zad-app.html"
```

Option B: Update existing app (like turquoise-rabbit-exploring):
```
Text to WEBTOYS: "--remix turquoise-rabbit-exploring use the HTML from agent-issue-tracker/issue-tracker-zad-app.html"
```

### 2. Configure Environment

Add to your `.env.local` file:
```bash
ISSUE_TRACKER_APP_ID=turquoise-rabbit-exploring  # Or your app's ID
PROJECT_ROOT=/path/to/your/project
ENABLE_AUTO_FIX=false  # Set to true when ready
AUTO_STASH=true
STRICT_GIT=false
```

### 3. Run Setup Script

```bash
cd agent-issue-tracker
./setup.sh
```

This will:
- Verify environment variables
- Check GitHub CLI authentication
- Create test scripts
- Set up logging

### 4. Test the System

Test reformulation only (safe):
```bash
./test-run.sh
```

Test full pipeline (dry run):
```

*[truncated — see source for full prompt]*