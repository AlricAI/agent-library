# TODO MANAGEMENT

> ## Overview

The Atlas TODO Management System provides a **unified single source of truth** for all tasks across the entire project. It solves the cri

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Atlas TODO Management System

## Overview

The Atlas TODO Management System provides a **unified single source of truth** for all tasks across the entire project. It solves the critical problem of scattered TODO tracking by automatically synchronizing with all external systems, ensuring no task is ever lost or forgotten.

## Problem Solved

**Before**: TODOs were scattered across multiple systems:
- Cursor TODO system (15 tasks)
- `dev_tasks.json` (5 tasks)
- Documentation files (78+ tasks)
- Inline code comments (TODO/FIXME/XXX/HACK)
- Checklist files (90+ tasks)
- Various roadmap files

**After**: **364+ TODOs** unified in a single system with bidirectional sync to all sources.

## System Architecture

### Single Source of Truth
- **`master_todos.json`** - Central repository for all TODOs
- **`scripts/unified_todo_manager.py`** - Core management system
- **`scripts/todo_api.py`** - CLI interface for external systems
- **`scripts/todo_helpers.py`** - Helper functions for programmatic access
- **Bidirectional sync** - Changes in any system automatically update all others

### Integration Points

The system automatically synchronizes with:

1. **Dev Workflow** (`dev_tasks.json`) - Development tasks and project milestones
2. **Documentation** - Task references in markdown files across docs/
3. **Checklists** - Unchecked items in YAML and markdown checklist files
4. **Inline Code** - TODO/FIXME/XXX/HACK comments in source code
5. **Health Checks** - Issues found by system monitoring and health checks
6. **Cursor System** - Tasks visible in Cursor's TODO UI
7. **Roadmap Files** - Tasks mentioned in various roadmap documents

## Core Features

### Intelligent Deduplication
- Prevents duplicate TODOs across systems
- Uses content similarity matching
- Maintains cross-references between systems
- Handles variations in task descriptions

### Priority Detection
- Automatically assigns priority based on keywords
- **Critical**: "critical", "urgent", "blocker", "broken"
- **

*[truncated — see source for full prompt]*