# Blog Series Discovery

> ## 🎯 Overview

📋 Blog series are defined as individual JSON configuration files in the `haskell/series/` directory.
🔍 The system auto-discovers all

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🔍 Blog Series Auto-Discovery — Declarative Configuration

## 🎯 Overview

📋 Blog series are defined as individual JSON configuration files in the `haskell/series/` directory.
🔍 The system auto-discovers all `.json` files at startup and derives everything needed to run each series.
🚀 Adding a new blog series requires only creating a single config file — no Haskell source changes.

## 🏗️ Architecture

### 📦 Components

| 🧩 Component | 📂 Path | 📝 Purpose |
|---|---|---|
| 🔍 Discovery | `haskell/src/Automation/BlogSeriesDiscovery.hs` | JSON config parser, validation, convention-based derivation |
| ⚙️ Series Config | `haskell/src/Automation/BlogSeriesConfig.hs` | Runtime-parameterized series metadata and lookup |
| 🗓️ Scheduler | `haskell/src/Automation/Scheduler.hs` | Dynamic schedule built from discovered series |
| 🚀 Runner | `haskell/app/RunScheduled.hs` | Discovers series at startup, builds dynamic task runners |

### 🔄 Data Flow

```
📂 haskell/series/*.json (config files on disk)
         ↓
🔍 discoverSeries(haskellDir) → [DiscoveredSeries]
         ↓
   ├─ deriveBlogSeriesConfig → BlogSeriesConfig (metadata)
   ├─ deriveBlogSeriesRunConfig → BlogSeriesRunConfig (models, env var)
   └─ deriveScheduleEntry → ScheduleEntry (task ID, hours)
         ↓
🗓️ buildSchedule(dynamicEntries) → full schedule (static + dynamic)
         ↓
🚀 taskRunners(context, seriesMap, runConfigs) → Map TaskId (IO ())
```

## 📄 Configuration Schema

📋 Each series is a JSON object in `haskell/series/{series-id}.json`.
🏷️ The series ID is derived from the filename (e.g., `garden-thoughts.json` becomes series ID `garden-thoughts`).
📦 Parsing uses the existing `Automation.Json` module with `FromValue` and the `(.:)` and `(.:?)` operators.

### 📝 Required Fields

| 🏷️ Field | 📊 Type | 📝 Description |
|---|---|---|
| `name` | string | Display name for the series |
| `icon` | string | Emoji icon for the series |
| `scheduleHourPacific` | number | Hour in Pacific time to g

*[truncated — see source for full prompt]*