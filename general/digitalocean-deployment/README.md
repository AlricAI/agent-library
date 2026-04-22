# DIGITALOCEAN DEPLOYMENT

> **Domain:** reesereviews.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Reese Reviews — DigitalOcean App Platform Deployment Guide

**Domain:** reesereviews.com  
**Platform:** DigitalOcean App Platform (Static Site)  
**Repo:** MIDNGHTSAPPHIRE/reese-reviews (branch: `main`)  
**Last Updated:** March 2026

---

## Overview

Reese Reviews is a React 18 + Vite + TypeScript frontend that connects to Supabase for data. It is deployed as a **Static Site** on DigitalOcean App Platform, which handles building, CDN delivery, SSL certificates, and custom domain routing automatically.

The App Platform configuration lives in `.do/app.yaml` at the root of this repository. Every push to `main` triggers an automatic redeploy.

---

## Architecture

```
GitHub (main branch)
        │
        ▼  auto-deploy on push
DigitalOcean App Platform
  └── Static Site: npm run build → dist/
        │
        ▼  CDN + SSL (auto)
  reesereviews.com  (CNAME → <app>.ondigitalocean.app)
```

---

## One-Time Setup: Deploy via Dashboard

If you do not have a DO API token configured, follow these steps in the DigitalOcean web dashboard:

### Step 1 — Create the App

1. Log in to [cloud.digitalocean.com](https://cloud.digitalocean.com)
2. Click **Apps** in the left sidebar
3. Click **Create App**
4. Choose **GitHub** as the source
5. Authorize DigitalOcean to access your GitHub account if prompted
6. Select repository: **MIDNGHTSAPPHIRE/reese-reviews**
7. Select branch: **main**
8. Check **Autodeploy** (so every push to main redeploys automatically)
9. Click **Next**

### Step 2 — Configure the Component

DigitalOcean will auto-detect the Vite project. Confirm or set these values:

| Setting | Value |
|---|---|
| **Component type** | Static Site |
| **Build command** | `npm run build` |
| **Output directory** | `dist` |
| **Index document** | `index.html` |
| **Error document** | `index.html` |

> Setting the error document to `index.html` is critical — it enables React Router to handle all client-side routes without 404 errors.

### Step 3 — Set Environment Variable

*[truncated — see source for full prompt]*