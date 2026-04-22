# Scheduled Tasks

> ## 🎯 Overview

📋 All recurring automation tasks run through a single hourly GitHub Actions cron job.
🧠 A Haskell scheduler determines which tasks t

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ⏰ Scheduled Tasks — Consolidated Task Scheduler

## 🎯 Overview

📋 All recurring automation tasks run through a single hourly GitHub Actions cron job.
🧠 A Haskell scheduler determines which tasks to execute based on the current **Pacific** hour.
🚫 Zero scheduling logic lives in YAML — the workflow file is purely declarative.
🔄 Blog series and reflection-title use "at or after" scheduling with idempotency checks for resilience.

## 🏗️ Architecture

### 📦 Components

| 🧩 Component | 📂 Path | 📝 Purpose |
|---|---|---|
| 📚 Scheduler | `haskell/src/Automation/Scheduler.hs` | 🧠 Pure functions: given Pacific hour → task IDs to run |
| 🎯 Orchestrator | `haskell/app/RunScheduled.hs` | 🔧 Single entry point that calls library functions directly |
| ⚙️ Workflow | `.github/workflows/scheduled.yml` | 🕐 Hourly cron, declarative YAML only |

### 🔀 Haskell Implementation

🏗️ The Haskell orchestrator (RunScheduled.hs) is the sole implementation used in CI.
🐳 The executable is pre-built by the `haskell.yml` CI workflow (using the `haskell:9.14.1` Docker container) and uploaded as an artifact with 90 day retention.
🔍 The `haskell.yml` workflow only triggers on pushes that change files under `haskell/` or the workflow file itself, avoiding unnecessary builds.
🔄 The `haskell.yml` workflow uses `concurrency` with `cancel-in-progress: true` to automatically cancel superseded CI runs on the same branch.
⬇️ The scheduled workflow downloads the pre-built binary from the latest successful Haskell CI run — no compilation at runtime.
✅ Fully implemented task runners: blog-series (dynamically discovered), ai-fiction, reflection-title.
⚠️ Stubbed task runners (log and skip): backfill-blog-images, internal-linking, social-posting.

### 🔄 Data Flow

```
⏰ GitHub Actions cron (hourly)
         ↓
📜 bin/run-scheduled
         ↓
🧠 getScheduledTasks(nowPacificHour())
         ↓
📋 For each task (direct library calls, no subprocesses):
   ├── 📰 blog-series:the-noise         → chec

*[truncated — see source for full prompt]*