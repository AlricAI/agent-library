# Obsidian Sync

> ## 🎯 Overview

📋 Synchronizes the Obsidian vault between the cloud and the local filesystem using the `ob` CLI tool.
🔄 Uses a simple pull-edit-push

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 📱 Obsidian Sync — Vault Synchronization via ob CLI

## 🎯 Overview

📋 Synchronizes the Obsidian vault between the cloud and the local filesystem using the `ob` CLI tool.
🔄 Uses a simple pull-edit-push flow: one pull at the start, local edits, one push at the end.
🔒 Handles lock contention with retry logic and stale lock cleanup.
📝 Provides embed appending to write social media embeds to Obsidian notes.
🛡️ Pre-push circuit breaker prevents catastrophic data loss from anomalous file deletions.

## 🏗️ Architecture

### 📦 Components

| 🧩 Component | 📂 Path | 📝 Purpose |
|---|---|---|
| 📱 Sync Library | `haskell/src/Automation/ObsidianSync.hs` | 🔧 Vault sync, push, lock management, embed appending |

### 🔄 Data Flow — Scheduled Run

```
main()
  ├─ 📥 syncObsidianVault(credentials)     ← ONE pull at the start
  │       ├─ 📂 Create fresh vault directory (ephemeral CI — nothing exists yet)
  │       ├─ 📦 ob sync-setup → configure vault
  │       ├─ 🔄 ob sync → download all files
  │       └─ 📊 Record file count baseline
  │
  ├─ 🔧 Task 1: operates on vaultDir       ← Tasks receive vault dir
  ├─ 🔧 Task 2: operates on vaultDir
  ├─ 🔧 Task N: operates on vaultDir
  │
  └─ 📤 pushObsidianVault(vaultDir)        ← ONE push at the end
          ├─ 📊 Count files and validate against baseline
          ├─ 🛑 Circuit breaker: abort if any files lost
          └─ 🔄 ob sync to push changes
```

### 🔄 Data Flow — Standalone Scripts

```
📥 syncObsidianVault(credentials)      ← Pull
     ↓
📝 Edit files locally
     ↓
📤 pushObsidianVault(vaultDir)         ← Push
```

## 🛡️ Data Loss Prevention

### 📂 Ephemeral Vault Directory

🏗️ Every scheduled run executes in a fresh ephemeral CI container with no pre-existing vault directory.
📂 `syncObsidianVault` creates a new directory via `ob sync-setup` and populates it with `ob sync`.
🚫 No files are ever deleted — this system only creates and edits files.
⚠️ **Root Cause (2026-03-27 incident):** Bidirectional `ob

*[truncated — see source for full prompt]*