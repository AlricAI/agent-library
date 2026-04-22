# Blog Generation

> ## 🎯 Overview

📋 Generates daily AI-written blog posts for six distinct blog series.
🧠 Constructs rich prompts from post history, reader comments, 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 📝 Blog Generation — AI-Powered Blog Series Pipeline

## 🎯 Overview

📋 Generates daily AI-written blog posts for six distinct blog series.
🧠 Constructs rich prompts from post history, reader comments, and calendar-aware recap detection.
📅 Includes deterministic human-readable date (day of week, month, day, year) in every prompt for date awareness.
🔧 Assembles YAML frontmatter with navigation links, slugs, and model signatures.
🗂️ Manages series configuration, post parsing, and index generation for each series.

## 🏗️ Architecture

### 📦 Components

| 🧩 Component | 📂 Path | 📝 Purpose |
|---|---|---|
| 🕐 Pacific Time | `haskell/src/Automation/PacificTime.hs` | 📅 Shared Pacific timezone logic: formatDay, formatDayHuman, todayPacificDay, pacificHour |
| 🧠 Prompt Builder | `haskell/src/Automation/BlogPrompt.hs` | 🔧 Constructs system and user prompts from blog context with recap awareness |
| 📚 Series Logic | `haskell/src/Automation/BlogSeries.hs` | 🔄 Context assembly, post parsing, index generation, navigation linking |
| 📄 Post Reader | `haskell/src/Automation/BlogPosts.hs` | 📖 Reads and parses markdown posts from series directories |
| ⚙️ Series Config | `haskell/src/Automation/BlogSeriesConfig.hs` | 🗺️ Runtime-parameterized series metadata lookup |
| 🔍 Discovery | `haskell/src/Automation/BlogSeriesDiscovery.hs` | 🔍 Dhall config parser, validation, convention-based derivation |

### 🔄 Data Flow

```
⚙️ Series Config (BLOG_SERIES map)
         ↓
📚 buildBlogContext(seriesId, repoRoot, comments, today)
         ↓
   ├─ 📄 readSeriesPosts(seriesDir) → sorted BlogPost[]
   ├─ 📖 readAgentsMd(seriesDir) → system prompt override
   └─ 🗨️ filterCommentsAfterLastPost() → relevant BlogComment[]
         ↓
🧠 buildBlogPrompt(context) → { system, user }
         ↓
   ├─ 📜 buildPostHistory() → full recent + title-only older posts
   ├─ 💬 buildCommentsSection() → priority-flagged comments
   └─ 📅 recapInstructions() → weekly/monthly/quarterly/annual rec

*[truncated — see source for full prompt]*