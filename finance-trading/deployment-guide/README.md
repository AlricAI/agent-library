# DEPLOYMENT GUIDE

> Complete step-by-step deployment instructions for Pact Marketplace to staging and production environments.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Deployment Guide

Complete step-by-step deployment instructions for Pact Marketplace to staging and production environments.

---

## Pre-Deployment Checklist

- [ ] All tests passing: `npm test`
- [ ] Build successful: `npm run build`
- [ ] No TypeScript errors
- [ ] No ESLint warnings
- [ ] All environment variables configured
- [ ] Database migrations reviewed and tested locally
- [ ] Edge functions code reviewed
- [ ] Paystack webhook URLs updated
- [ ] Sentry/monitoring configured
- [ ] Backup of production database scheduled

---

## Environment Variables

Create `.env.local` with these values:

```bash
# Supabase
NEXT_PUBLIC_SUPABASE_URL=https://<project>.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=<anon_key>
SUPABASE_SERVICE_ROLE_KEY=<service_role_key>

# Paystack
NEXT_PUBLIC_PAYSTACK_PUBLIC_KEY=<public_key>
PAYSTACK_SECRET_KEY=<secret_key>

# Cron/Edge Functions
CRON_SECRET=<random_secret_for_webhook_auth>

# Optional: Monitoring
SENTRY_AUTH_TOKEN=<if_using_sentry>
SENTRY_ORG=<org>
SENTRY_PROJECT=<project>
```

### Obtaining Keys

1. **Supabase:**
   - Dashboard → Project Settings → API
   - Copy `NEXT_PUBLIC_SUPABASE_URL` and `NEXT_PUBLIC_SUPABASE_ANON_KEY`
   - Service role key under "Service role" tab

2. **Paystack:**
   - Dashboard → Settings → API Keys & Webhooks
   - Copy live/test keys based on environment
   - Configure webhook URL: `https://<your-domain>/api/payments/webhook`

3. **Cron Secret:**
   - Generate: `openssl rand -hex 32`
   - Store securely (use Supabase secrets or similar)

---

## Staging Deployment

### 1. Database Setup

```bash
# Connect to staging Supabase project
# Dashboard → SQL Editor → run these migrations in order:

-- 1. Check existing tables
SELECT table_name FROM information_schema.tables 
WHERE table_schema = 'public';

-- 2. Apply migrations (in order):
-- a. process_pool_lock RPC
-- b. create_orders_for_pool RPC
-- c. deduct_pool_inventory R

*[truncated — see source for full prompt]*