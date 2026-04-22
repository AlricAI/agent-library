# Ai Fiction

> ## 🎯 Overview

📋 Generates a short, emoji-rich AI fiction passage for each daily reflection note.
🧠 Themes are abstracted from the day's content — 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🤖🐲 AI Fiction — Automated Fiction in Daily Reflections

## 🎯 Overview

📋 Generates a short, emoji-rich AI fiction passage for each daily reflection note.
🧠 Themes are abstracted from the day's content — frontmatter and embed sections are stripped before prompting.
🤖 Uses a Gemini model chain with retry and fallback for resilience.
🕐 Runs at 10 PM Pacific (hour 22), before the reflection-title task in the same scheduling slot.
🧩 Fully idempotent — skips if `## 🤖🐲 AI Fiction` section already exists.

## 🏗️ Architecture

### 📦 Components

| 🧩 Component | 📂 Path | 📝 Purpose |
|---|---|---|
| 📚 Library | `haskell/src/Automation/AiFiction.hs` | 🔧 Pure functions for prompt building, response parsing, and content application |
| 🧪 Tests | `haskell/test/Automation/AiFictionTest.hs` | ✅ Tests covering all pure functions |
| ⏰ Scheduler entry | `haskell/src/Automation/Scheduler.hs` | 📅 `ai-fiction` task at hour 22 Pacific with `atOrAfter` |
| 🎛️ Orchestrator | `haskell/app/RunScheduled.hs` | 🔄 `runAiFiction` — vault sync, idempotency, Gemini call, write-back |

### 🔄 Data Flow

```
⏰ Scheduler (hour 22+ Pacific)
         ↓
🎛️ runAiFiction()
         ↓
📥 Pull Obsidian vault via syncObsidianVault()
         ↓
📄 Read today's reflection note (reflections/YYYY-MM-DD.md)
         ↓
🛡️ reflectionNeedsFiction(content) → skip if ## 🤖🐲 AI Fiction exists
         ↓
🧹 stripForPrompt(content) → remove frontmatter + embed sections
         ↓
🧠 buildFictionPrompt(strippedContent) → structured Gemini prompt
         ↓
🤖 generateFiction(apiKey, models, prompt) → call Gemini with model chain
         ↓
📋 parseFictionResponse(raw) → clean and validate response
         ↓
📝 applyFiction(content, fiction) → insert section before embeds/updates
         ↓
💾 Write updated reflection + push vault
```

## ⏰ Schedule

- **Hour**: 22 Pacific (10 PM PST / PDT)
- **Semantics**: At-or-after — eligible at hour 22 and all subsequent hours until 11:59 PM Pacific
- **Orderin

*[truncated — see source for full prompt]*