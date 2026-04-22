# Safety Feature Api Requirements

> ## Overview

This document outlines the API requirements needed to support the enhanced safety features designed for YouAndINotAI. These requirements 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# API Requirements for Enhanced Safety Features

## Overview

This document outlines the API requirements needed to support the enhanced safety features designed for YouAndINotAI. These requirements should be reviewed with the CTO (b02a21c7-737e-4177-91ac-6d8e57805801) for implementation.

## 1. Enhanced SafetyDrawer Features

### New Endpoints Needed:

- POST /api/safety/block - Block a user
- POST /api/safety/mute - Mute a user temporarily
- POST /api/safety/restrict - Restrict user visibility
- POST /api/safety/freeze - Freeze conversation
- GET /api/safety/status/{userId} - Get safety status indicators

### Updated Endpoints:

- POST /api/report - Enhanced reporting with additional context fields

## 2. Enhanced ReportForm Features

### New Fields for Report Endpoint:

- date: Date when incident occurred
- evidence: Array of evidence file IDs
- urgency: Enum (not_urgent, serious, critical)
- context: Object containing boolean flags for additional context
- reason_details: Detailed categorization of report reason

### New Endpoints:

- POST /api/evidence/upload - Upload evidence files for reports
- GET /api/evidence/{id} - Retrieve evidence file metadata
- DELETE /api/evidence/{id} - Remove evidence file

## 3. BlockConfirmationDialog Features

### Updated Endpoints:

- POST /api/safety/block - Enhanced with undo functionality
- POST /api/safety/unblock - Unblock a user
- POST /api/safety/mute - Alternative action endpoint
- POST /api/safety/restrict - Alternative action endpoint

### New Endpoints:

- POST /api/safety/undo-block - Undo block within time window
- GET /api/safety/blocked-users - Retrieve list of blocked users

## 4. SafetyTipBanner Features

### New Endpoints:

- GET /api/safety/tips - Retrieve relevant safety tips for user
- POST /api/safety/tips/dismiss - Dismiss a specific tip
- GET /api/safety/tips/{id} - Retrieve specific tip details

## 5. General Safety Feature Requirements

### Authentication and Authorization:

- All safety endpoints requ

*[truncated — see source for full prompt]*