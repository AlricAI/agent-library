# VK OPTIMIZATION README

> This directory contains SQL scripts to optimize Vibe-Kanban database performance.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Vibe-Kanban Database Optimization Scripts

This directory contains SQL scripts to optimize Vibe-Kanban database performance.

## Quick Start - Immediate Performance Fix

Run the optimization script to add indexes and enable WAL mode:

```bash
# Find your VK database file (usually in ~/.vibe-kanban/ or project data directory)
VK_DB="$HOME/.vibe-kanban/data/vibe-kanban.db"

# Run optimization (takes ~30 seconds)
sqlite3 "$VK_DB" < scripts/optimize-vk-db.sql
```

**Expected Result:** 70-80% reduction in query times immediately.

## Scripts

### 1. `optimize-vk-db.sql` - Immediate Performance Boost

**What it does:**
- Adds critical indexes on foreign keys
- Enables WAL (Write-Ahead Logging) mode for better concurrency
- Increases cache size to 64MB
- Updates query planner statistics

**When to run:**
- Immediately if VK is slow
- After any major database schema changes
- Monthly as preventive maintenance

**Expected impact:**
- Task list queries: 1-3s → 200-400ms
- Better write concurrency (readers don't block writers)
- No downtime required (can run while VK is running)

### 2. `archive-vk-data.sql` - Database Size Reduction

**What it does:**
- Archives completed tasks older than 30 days to `tasks_archive` table
- Archives logs older than 7 days to `execution_process_logs_archive` table
- Cleans up orphaned records (sessions, execution_processes for deleted workspaces)
- Runs VACUUM to reclaim disk space

**When to run:**
- Weekly or monthly (depending on task volume)
- When database size > 500MB
- When you notice slowing performance over time

**Expected impact:**
- Database size: -60-80% (e.g., 500MB → 100-150MB)
- Query times: Additional 20-30% improvement
- Keeps only recent data in active tables

**⚠️ Important:**
- Stop VK before running this script (it needs exclusive access for VACUUM)
- Backup database first: `cp vibe-kanban.db vibe-kanban.db.backup`
- Can take 5-15 minutes depending on database size

```bash
# Stop VK
pkill -f vibe-kanban

# Backup databa

*[truncated — see source for full prompt]*