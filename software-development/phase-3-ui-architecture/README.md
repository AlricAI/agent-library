# PHASE 3 UI ARCHITECTURE

> **Created**: 2026-02-03
**Status**: Approved design for golden path UI

## Overview

This document defines the information architecture for the CodeFR

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CodeFRAME Phase 3: UI Information Architecture

**Created**: 2026-02-03
**Status**: Approved design for golden path UI

## Overview

This document defines the information architecture for the CodeFRAME web UI. The UI follows the "golden path" philosophy - we build only what's necessary for the core workflow, nothing more.

**Key Constraints:**
- CLI is fully functional and production-ready (Phase 1 complete)
- REST API with SSE streaming is complete (Phase 2 complete)
- UI should consume existing API, not drive new features
- Tech stack: Next.js App Router, Shadcn/UI + Tailwind (Nova template), Hugeicons

---

## 1. View Inventory

### 1.1 Workspace View (Home)
**Purpose:** Initialize and overview the current workspace state.

**Key Actions:**
- Initialize workspace (one-time setup per repo)
- View workspace metadata (tech stack, git status)
- Quick access to PRD, tasks, and active runs

**Data Displayed:**
- Workspace path and initialization status
- Detected tech stack configuration
- Quick stats: PRD count, task counts by status, active runs
- Recent activity timeline (last 5 events)

---

### 1.2 PRD View
**Purpose:** Create, view, and iterate on Product Requirements Documents.

**Key Actions:**
- Upload/paste PRD markdown
- Start discovery session (Socratic AI conversation)
- Edit PRD content
- Generate tasks from PRD

**Data Displayed:**
- PRD content (markdown rendered)
- PRD metadata (version, created date, file path)
- Discovery session transcript (if applicable)
- Associated tasks count and status breakdown

---

### 1.3 Task Board View
**Purpose:** Visualize and manage task lifecycle from backlog to completion.

**Key Actions:**
- View tasks grouped by status (BACKLOG, READY, IN_PROGRESS, DONE, BLOCKED, FAILED)
- Filter/search tasks
- Execute single task
- Start batch execution
- View task details
- Mark tasks as READY manually

**Data Displayed:**
- Kanban-style columns (or simple list grouped by status)
- Per-task cards showing: title, description sni

*[truncated — see source for full prompt]*