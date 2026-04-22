# DEPLOYMENT

> This project uses manual GitHub Actions deployments for the backend via Vercel and a manual release process for the mobile app (APK) via GitHub Actions + Expo EAS.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Deployment & Release Runbook

This project uses manual GitHub Actions deployments for the backend via Vercel and a manual release process for the mobile app (APK) via GitHub Actions + Expo EAS.

## 🌿 Branching & Environment Strategy

- **`develop` branch**: Default working branch.
  - **Backend Deploy**: Trigger the manual backend workflow and choose `stage`.
  - **Mobile App**: Local development (`pnpm dev`, `expo run:android`) automatically targets the staging backend url.
  
- **`main` branch**: Production branch.
  - **Backend Deploy**: Trigger the manual backend workflow and choose `prod`.
  - **Mobile App**: Production EAS builds target the production backend url.

## 🚀 Workflows

### 1. Backend Deploy (Vercel)
**File**: `.github/workflows/backend-deploy.yml`

This workflow is **manual only** (via `workflow_dispatch`) and can run from any branch.
- It uses a single fast job with the Vercel CLI (`vercel pull`, `vercel build`, `vercel deploy`).
- It deploys to a single Vercel project (`VERCEL_PROJECT_ID_SERVER`), with environment selected by input:
  - `stage` -> Vercel `preview`
  - `prod` -> Vercel `production` (`--prod`)
- Concurrent runs for the same branch + environment are automatically canceled to save CI time.

**How to deploy backend manually:**
1. Go to the **Actions** tab in GitHub.
2. Select **Backend Deploy**.
3. Click **Run workflow**.
4. Choose the branch to deploy from.
5. Choose environment: `stage` or `prod`.
6. Click **Run workflow**.

### 2. Mobile APK Release (Expo EAS)
**File**: `.github/workflows/mobile-release.yml`

This workflow is **manual only** (via `workflow_dispatch` in the GitHub Actions tab) to prevent CI spam and cost on every commit.

**How to create a release:**
1. Go to the **Actions** tab in GitHub.
2. Select **Mobile APK Release** on the left.
3. Click **Run workflow**.
4. Enter the release **Tag** you want to create (e.g., `v1.2.0`).
5. Choose the branch (usually `main`).
6. Click **Run workflow**.

**What it does:**
- 

*[truncated — see source for full prompt]*