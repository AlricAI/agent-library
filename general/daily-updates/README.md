# Daily Updates

> ## 🎯 Overview

📋 When files are modified by automated tasks (image backfill, internal linking, auto-posting), a wiki link to each modified file is r

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🔄 Daily Updates — Changes Directory

## 🎯 Overview

📋 When files are modified by automated tasks (image backfill, internal linking, auto-posting), a wiki link to each modified file is recorded in a daily changes page at `changes/YYYY-MM-DD.md`.
🔁 Replaces the old approach of writing updates directly into the daily reflection note, reducing Enveloppe plugin link-checking overhead.
📂 Each day gets its own changes page in the `changes/` directory, named after the date (matching the reflection page naming convention).
🪞 Each reflection page links to its corresponding changes page at the bottom.
📱 Optimized for Obsidian mobile — reflections stay lightweight while changes are a click away.
🧩 Fully idempotent — links and details already present are silently skipped.
📊 A stats line at the top summarizes total counts per update type.
📐 Updates are rendered as a compact markdown table with one row per page and emoji column headers.

## 🏗️ Architecture

### 📦 Components

| 🧩 Component | 📂 Path | 📝 Purpose |
|---|---|---|
| 📚 Library | `haskell/src/Automation/DailyUpdates.hs` | 🔧 Typed update details, parse/merge/render pipeline, changes page management |
| 📚 Library | `haskell/src/Automation/DailyReflection.hs` | 🪞 Reflection template with changes link, trailing section ordering |
| 🧪 Tests | `haskell/test/Automation/DailyUpdatesTest.hs` | ✅ Tests covering table format, stats, migration, idempotency, changes directory |
| 🧪 Tests | `haskell/test/Automation/DailyReflectionTest.hs` | ✅ Tests covering reflection template with changes link |
| 🔌 Consumers | `haskell/src/Automation/SocialPosting.hs` | 📢 Adds `PostedTo` details after social media posting |
| 🔌 Consumers | `haskell/app/RunScheduled.hs` | 🖼️🔗 Adds `ImageAdded` and `InternalLinksAdded` details |

### 🔄 Data Flow

```
🖼️ backfill-blog-images / 🔗 internal-linking / 📢 auto-post
         ↓
📂 Collect modified file paths + build typed UpdateDetail values
         ↓
🔧 addUpdateLinksToReflecti

*[truncated — see source for full prompt]*