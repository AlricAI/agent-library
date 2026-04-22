# Github Workflows Design

> ## Executive Summary

This document provides a comprehensive design for implementing GitHub Actions workflows to automate testing and deployment for t

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# GitHub Actions Workflow Design for CodeFRAME

## Executive Summary

This document provides a comprehensive design for implementing GitHub Actions workflows to automate testing and deployment for the CodeFRAME project across three environments: Development, Staging, and Production.

## Environment Definitions

Based on the current project structure and configuration:

1. **Development Environment** (Local Development)
   - Local machine development with hot-reload
   - Database: `.codeframe/state.db` (local)
   - No automated deployment needed (local only)

2. **Staging Environment** (Current "staging", what you call development)
   - Internal testing environment with PM2 process manager
   - Backend Port: 14200
   - Frontend Port: 14100
   - Database: `staging/.codeframe/state.db`
   - Deployment: Automated on push to `staging` or `development` branch
   - Access: Internal network only

3. **Production Environment** (Public IP, what you call staging)
   - Public-facing environment with public IP access
   - Backend Port: TBD (suggest 8200)
   - Frontend Port: TBD (suggest 8100)
   - Database: `production/.codeframe/state.db`
   - Deployment: Manual approval required, triggered from `main` branch
   - Access: Public internet

## Workflow Architecture

### 1. Testing Workflow (Continuous Integration)
**File**: `.github/workflows/ci-tests.yml`
**Triggers**: Push to any branch, Pull Request to main/staging/development

```
┌─────────────────────────────────────────────────────┐
│              CI Testing Pipeline                     │
├─────────────────────────────────────────────────────┤
│                                                      │
│  1. Code Checkout                                   │
│  2. Python Setup (3.11+)                            │
│  3. Node.js Setup (18+)                             │
│  4. Install Python Dependencies (uv/pip)            │
│  5. Install Node Dependencies (npm)                 │
│  6. Linting & Type Checking                    

*[truncated — see source for full prompt]*