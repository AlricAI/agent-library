# Daily Reflection

> ## 🎯 Overview

📋 Automatically creates and updates daily reflection notes in the Obsidian vault when blog posts are generated.
🤖 Entirely determini

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 📝 Daily Reflection Auto-Update

## 🎯 Overview

📋 Automatically creates and updates daily reflection notes in the Obsidian vault when blog posts are generated.
🤖 Entirely deterministic — no AI required.
🔗 Eliminates the manual step of linking new blog posts from daily reflection notes.

## 🏗️ Architecture

### 📦 Components

| 🧩 Component | 📂 Path | 📝 Purpose |
|---|---|---|
| 📚 Library | `haskell/src/Automation/DailyReflection.hs` | 🔧 Pure functions for reflection creation and post link insertion |
| 🧪 Tests | `haskell/test/Automation/DailyReflectionTest.hs` | ✅ 40 tests covering all pure and I/O functions |
| 🔌 Integration | `haskell/app/RunScheduled.hs` | 📝 Calls reflection update after generating a post |
| ⚙️ Workflow | `.github/workflows/scheduled.yml` | 🤖 Consolidated hourly cron (runs all blog series) |

### 🔄 Data Flow

```
📝 RunScheduled.hs (blog generation)
         ↓
🤖 Generate blog post (Gemini AI)
         ↓
💾 Write post file to series dir
         ↓
📎 Write exact path to $GITHUB_OUTPUT
         ↓
🔑 Check for OBSIDIAN_AUTH_TOKEN + OBSIDIAN_VAULT_NAME
         ↓ (if available)
☁️ Sync Obsidian Vault (pull)
         ↓
📄 Ensure daily reflection exists
   ├── 🆕 Create from template if missing
   └── 🔗 Add forward link to previous day
         ↓
📎 Insert post link in reflection
   ├── 📌 Create series section if missing
   └── ➕ Append link to existing section
         ↓
☁️ Push Obsidian Vault
```

## 📐 Reflection Template

### 📄 Generated Frontmatter

```yaml
---
share: true
aliases:
  - YYYY-MM-DD
title: YYYY-MM-DD
URL: https://bagrounds.org/reflections/YYYY-MM-DD
Author: "[[bryan-grounds]]"
tags:
---
```

### 🧭 Navigation Line

```
[[index|Home]] > [[reflections/index|Reflections]] | [[reflections/PREV-DATE|⏮️]] [[reflections/NEXT-DATE|⏭️]]
```

⏮️ Back links are added when a previous reflection exists. ⏭️ Forward links are added to the previous day's reflection when a new day is created. Both work even on the first reflectio

*[truncated — see source for full prompt]*