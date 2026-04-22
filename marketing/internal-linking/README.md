# Internal Linking

> ## 🎯 Overview

📋 Automatically inserts wikilinks into content files by identifying genuine book references with Gemini AI.
🧭 Uses BFS traversal sta

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🔗 Internal Linking — BFS Wikilink Insertion

## 🎯 Overview

📋 Automatically inserts wikilinks into content files by identifying genuine book references with Gemini AI.
🧭 Uses BFS traversal starting from the most recent reflection to prioritize recently active files.
⏱️ Spends up to 10 inference calls per run to maximize linking coverage within API quota limits.
🛡️ Tracks analysis state in frontmatter to skip already-processed files across sessions.
📖 Supports subtitle-aware matching: books referenced by main title (without subtitle) are correctly detected and linked with the full book title.

## 🏗️ Architecture

### 📦 Components

| 🧩 Component | 📂 Path | 📝 Purpose |
|---|---|---|
| 🔗 Library | `haskell/src/Automation/InternalLinking.hs` | 🔧 BFS traversal, Gemini identification, wikilink insertion, frontmatter tracking |
| 🧪 Tests | `haskell/test/Automation/InternalLinkingTest.hs` | ✅ 160+ tests covering all pure functions and logic |
| ⏰ Scheduler entry | `haskell/src/Automation/Scheduler.hs` | 📅 Internal linking task scheduled in the pipeline |

### 🔄 Data Flow

```
🏗️ run(config: LinkingConfig)
         ↓
📇 buildContentIndex(contentDir) → ContentEntry[] from books/ (with mainTitle for subtitle-bearing titles)
         ↓
🧭 bfsTraversal(contentDir)
   ├─ 🔍 findMostRecentReflection() → start node
   └─ 🔗 extractLinkedPaths() → follow wikilinks + markdown links
         ↓
📄 For each file in BFS order (limit: 10 inference calls per run):
   ├─ 🛡️ alreadyAnalyzed(content) → skip if processed (unless force_analyze_links)
   ├─ 🧹 maskProtectedRegions(content) → hide frontmatter, code, links, headings
   ├─ 🤖 identifyBooksWithGemini(body, entries, path, apiKey, model)
   ├─ 🔍 findLinkCandidates(content, masked, index, existing, path)
   │     computes extractMainTitle on-the-fly; tries full plainTitle first, then subtitle prefix fallback
   └─ ✏️ applyReplacements(content, candidates, validations) — always uses full book title in wikilink
      

*[truncated — see source for full prompt]*