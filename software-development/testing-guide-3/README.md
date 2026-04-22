# Testing Guide

> > Last updated: v3.3.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Cue — Manual Testing Guide

> Last updated: v3.3.0
> Covers all 9 action types across all 4 placements, categories, per-project appearance, and property key namespace

---

## Prerequisites

```shell
# Use Node 22 (required)
export PATH="/opt/homebrew/opt/node@22/bin:$PATH"
node --version  # must print v22.x.x

forge login
NODE_OPTIONS="--max-old-space-size=8192" forge deploy --environment production
forge install --upgrade --non-interactive --confirm-scopes --environment production \
  --site narendev.atlassian.net --product jira
```

## Pre-commit Checks

1. `npx tsc --noEmit` — must pass with zero errors
2. `forge lint` — must pass with zero errors (warnings for deprecated `app.name` and `storage` are pre-existing and acceptable)
3. No `any` types in TypeScript files
4. No direct `storage.get()` / `storage.set()` calls outside `src/storage/client.ts`
5. No `requestJira()` calls on component render — only on button click or in the resolver

---

## Test 1 — Global Admin UI

### T1.1: Categories — Create
1. Open **Jira Settings → Apps → Cue — Smart Actions & Buttons**
2. Click **+ Add Category**, type "Escalation", click **Create**
3. **Expected:** "Escalation" category box appears (collapsed or open), shows "0 buttons"
4. Click **+ Add Category**, type "Onboarding", click **Create**
5. **Expected:** Two category boxes visible

### T1.2: Categories — Rename
1. Click **Rename** on the "Escalation" box
2. Change name to "Escalation & Triage", click **Save**
3. **Expected:** Box header updates immediately

### T1.3: Category Accordion (expand/collapse)
1. Click **▼** on a category box header
2. **Expected:** Box collapses, icon changes to **▶**
3. Click **▶** to re-expand
4. **Expected:** Box opens showing its buttons (or empty message)

### T1.4: Create Button — OPEN_URL (in category)
1. Click **+ Create Button**
2. Fill: Label = "Open Runbook", Style = Primary, Category = "Escalation & Triage", Action Type = Open URL
3. URL: `https://wiki.example.com/{{project.key

*[truncated — see source for full prompt]*