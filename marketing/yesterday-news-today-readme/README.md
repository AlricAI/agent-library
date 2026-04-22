# YESTERDAY NEWS TODAY README

> **Location:** 9020 node (DESKTOP-UPSJEVG)  
**Authority:** Josh Coleman  
**Date:** 2026-03-19  
**Purpose:** Automated daily news recap content for Y

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Yesterday's News Today - YouTube Automation Bot

**Location:** 9020 node (DESKTOP-UPSJEVG)  
**Authority:** Josh Coleman  
**Date:** 2026-03-19  
**Purpose:** Automated daily news recap content for YouTube

---

## Overview

This bot generates daily "Yesterday's News Today" content for YouTube. It:

1. Fetches yesterday's headlines from news sources
2. Generates a script and video project
3. Posts to YouTube Community tab (or uploads video when ready)
4. Runs on 9020 as a scheduled task

---

## File Structure

```
C:\Antigravity\scripts\yesterday-news-today.py              # Main bot (repo)
C:\Antigravity\scripts\start-yesterday-news.bat            # Manual startup (repo)
C:\Antigravity\scripts\setup-yesterday-news-scheduler.ps1  # Task scheduler setup (repo)
C:\Users\<user>\Documents\ANTIGRAVITY-RUNTIME\logs\yesterday-news-today.log   # Execution log
C:\Users\<user>\Documents\ANTIGRAVITY-RUNTIME\yesterday-news\content\          # Generated content
C:\Users\<user>\Documents\ANTIGRAVITY-RUNTIME\yesterday-news\archive\          # Archived content
C:\Users\<user>\Documents\ANTIGRAVITY-RUNTIME\yesterday-news\state.json        # Bot state
```

---

## Installation on 9020

### Step 1: Deploy files to 9020

From Sabretooth, copy files via SSH:

```powershell
# Copy bot script
scp C:\ANTIGRAVITY\scripts\yesterday-news-today.py 9020:C:\Antigravity\scripts\

# Copy startup script
scp C:\ANTIGRAVITY\scripts\start-yesterday-news.bat 9020:C:\Antigravity\scripts\

# Copy scheduler setup
scp C:\ANTIGRAVITY\scripts\setup-yesterday-news-scheduler.ps1 9020:C:\Antigravity\scripts\
```

### Step 2: Create directories on 9020

```powershell
ssh 9020 "mkdir %USERPROFILE%\Documents\ANTIGRAVITY-RUNTIME\logs 2>nul & mkdir %USERPROFILE%\Documents\ANTIGRAVITY-RUNTIME\yesterday-news\content 2>nul & mkdir %USERPROFILE%\Documents\ANTIGRAVITY-RUNTIME\yesterday-news\archive 2>nul"
```

### Step 3: Set up scheduled task (run on 9020)

```powershell
ssh 9020 "powershell -ExecutionPolicy Bypass -

*[truncated — see source for full prompt]*