# DEPLOYMENT CHECKLIST

> Quick reference for deploying the Polymarket data sync cron job to Vercel.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Deployment Checklist - Polymarket Cron Job

Quick reference for deploying the Polymarket data sync cron job to Vercel.

## Pre-Deployment

- [x] Created cron endpoint: `/app/api/cron/sync-markets/route.ts`
- [x] Created incremental sync function: `/packages/investing/src/prediction/sync/incremental-markets.ts`
- [x] Added exports to prediction index
- [x] Created `vercel.json` with cron configuration
- [x] Added documentation files
- [x] Build successful ✅

## Deployment Steps

### 1. Set Environment Variable in Vercel

```bash
# Generate a secure secret
openssl rand -base64 32

# Copy the output, then:
# 1. Go to Vercel Dashboard
# 2. Select your project
# 3. Go to Settings → Environment Variables
# 4. Add new variable:
#    Name: CRON_SECRET
#    Value: <paste the generated secret>
#    Environment: Production, Preview, Development
```

### 2. Deploy to Vercel

```bash
# Deploy to production
vercel --prod

# Or push to main branch (if connected to git)
git add .
git commit -m "Add Polymarket cron job for automated data sync"
git push origin main
```

### 3. Verify Deployment

Check that the cron job is active:
1. Go to Vercel Dashboard
2. Navigate to: Project → Settings → Cron Jobs
3. Verify: `/api/cron/sync-markets` appears with schedule `*/15 * * * *`

### 4. Test the Endpoint

```bash
# Replace with your values
CRON_SECRET="your_secret_here"
DOMAIN="your-domain.vercel.app"

# Test the endpoint
curl -H "Authorization: Bearer $CRON_SECRET" \
     https://$DOMAIN/api/cron/sync-markets
```

Expected response:
```json
{
  "success": true,
  "markets": 1000,
  "pricePoints": 45000,
  "priceHistoryUpdates": 950,
  "holders": 12500,
  "holderUpdates": 980,
  "duration": "85.42s",
  "message": "Successfully synced...",
  "cronJob": true,
  "timestamp": "2026-01-24T12:00:00.000Z"
}
```

### 5. Monitor First Executions

Watch the logs for the first few cron executions:
```bash
vercel logs --follow
```

Or in Vercel Dashboard:
- Deployments → Latest → Functions → `/api/c

*[truncated — see source for full prompt]*