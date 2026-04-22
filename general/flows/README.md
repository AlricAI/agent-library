# FLOWS

> The Flows API provides high-level operations for managing GitHub repositories and workflows at scale.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Flows API Documentation

The Flows API provides high-level operations for managing GitHub repositories and workflows at scale.

## Overview

The Flows API is designed to automate the setup and maintenance of GitHub repositories with standard configurations, particularly for Cloudflare Worker projects.

## Endpoints

### POST /api/flows/create-new-repo

Creates a new GitHub repository with default GitHub Actions workflows pre-configured.

**Request Body:**
```json
{
  "owner": "string",           // Required: Organization or user name
  "name": "string",            // Required: Repository name
  "description": "string",     // Optional: Repository description
  "private": boolean,          // Optional: Whether repo is private (default: false)
  "auto_init": boolean         // Optional: Initialize with README (default: true)
}
```

**Response:**
```json
{
  "repo": {
    "id": 123456,
    "name": "my-worker",
    "full_name": "my-org/my-worker",
    "html_url": "https://github.com/my-org/my-worker",
    "private": false
  },
  "workflows": [
    {
      "path": ".github/workflows/pr-comment-extractor.yml",
      "status": "success",
      "message": "Created"
    },
    {
      "path": ".github/workflows/deploy-worker.yml",
      "status": "success",
      "message": "Created"
    }
  ],
  "secrets": [
    {
      "name": "CLOUDFLARE_API_TOKEN",
      "status": "skipped",
      "message": "Secret encryption not implemented - use GitHub CLI or manual setup"
    },
    {
      "name": "CLOUDFLARE_ACCOUNT_ID",
      "status": "skipped",
      "message": "Secret encryption not implemented - use GitHub CLI or manual setup"
    }
  ]
}
```

**Default Workflows:**

1. **PR Comment Extractor** (`.github/workflows/pr-comment-extractor.yml`)
   - Automatically extracts and summarizes all PR comments
   - Cleans and formats feedback for AI bot consumption
   - Posts consolidated summary as a PR comment
   - Triggers on: `issue_comment`, `pull_request_review_comment`

2. **Clou

*[truncated — see source for full prompt]*