# ROLLOUT PLAN

> **Repository:** `midnghtsapphire/reese-reviews`
**Last Updated:** April 5, 2026
**Live URL:** https://reesereviews.com
**Hosting:** DigitalOcean App P

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Rollout Plan — Reese Reviews

**Repository:** `midnghtsapphire/reese-reviews`
**Last Updated:** April 5, 2026
**Live URL:** https://reesereviews.com
**Hosting:** DigitalOcean App Platform (auto-deploys on merge to `main`)

---

## Overview

`reesereviews.com` is a live, active application. Every merge to `main` triggers an automatic deployment. This document defines the safe process for rolling out new features and the rollback procedure for reverting a bad deployment.

---

## Deployment Architecture

```
Developer/Agent
    │
    ▼
Feature Branch  ──►  Pull Request  ──►  CI Checks (lint, typecheck, test, build)
                                              │
                                              ▼ (all pass)
                                        Merge to main
                                              │
                                              ▼
                                   GitHub Actions deploy.yml
                                              │
                                              ▼
                                DigitalOcean App Platform
                                    (production build)
                                              │
                                              ▼
                                    reesereviews.com live
```

**Pipeline steps in `ci.yml`:** ESLint → TypeScript typecheck → Vitest → Vite build  
**Deployment step in `deploy.yml`:** Triggered only on successful CI, pushes to DigitalOcean

---

## Pre-Deployment Checklist

Before merging any PR to `main`, verify all items below:

### Code Quality
- [ ] `npm run lint` exits 0 (no errors)
- [ ] `npm run typecheck` exits 0 (no TypeScript errors) — use `npx tsc --noEmit` if script not in package.json
- [ ] `npm test` — all tests pass
- [ ] `npm run build` — production build succeeds with no warnings about oversized chunks

### Feature Verification
- [ ] Feature works end-to-end in the browser at `http://localhost:5173` (dev mode)
- [ ] Feature w

*[truncated — see source for full prompt]*