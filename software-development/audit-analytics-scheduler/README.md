# AUDIT ANALYTICS SCHEDULER

> **Project**: Life Tracker
**Date**: 2026-01-14
**Auditor**: Claude Code (Senior Staff Engineer + Product Analytics Lead)
**Scope**: Complete audit of 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Analytics & Auto-Scheduler Audit Report

**Project**: Life Tracker
**Date**: 2026-01-14
**Auditor**: Claude Code (Senior Staff Engineer + Product Analytics Lead)
**Scope**: Complete audit of Analytics pipeline and Auto-Scheduler system

---

## Executive Summary

This audit reveals **critical gaps** in analytics data collection and calculation, along with timezone/reliability concerns in the Auto-Scheduler. The analytics dashboard is currently showing empty or minimal data despite user activity, indicating a **broken data pipeline** between data generation and analytics calculation.

### Critical Findings

1. **Analytics showing 0 hours despite completed time blocks** - Data exists but isn't being surfaced
2. **Plan vs Actual chart only showing 1 data point** (2026-01-06) instead of full date range
3. **No centralized event tracking** - analytics are calculated on-demand, not event-driven
4. **Auto-Scheduler lacks timezone awareness** - DST and timezone boundary bugs likely
5. **No observability** - debugging requires manual console.log archaeology
6. **Fragmented data sources** - Sessions vs TimeBlocks with inconsistent rollup logic

---

## A. CURRENT STATE OVERVIEW

### A1. Analytics Infrastructure

#### Providers & SDK Integration
- **No external analytics provider** (no GA4, PostHog, Mixpanel, etc.)
- **Custom implementation** using `src/lib/database.ts` analytics methods
- **Debug logging only** via `src/lib/analyticsDebug.ts` (dev-only console output)
- **No structured telemetry** or error tracking service (no Sentry, etc.)

#### Event Tracking Locations
Current "analytics" is **computed on-demand**, not event-based:

**File**: `src/components/MainApp.tsx:133-197`
- Loads analytics via `db.calculatePlanVsActualData()`
- Loads on mount + when `timeRange` changes
- **Problem**: Expensive recalculation every time, no event-driven updates

**File**: `src/lib/database.ts` (LifeTrackerDB class)
- `calculatePlanVsActualData()` - Line 512-653
- `calculateTimeAlloca

*[truncated — see source for full prompt]*