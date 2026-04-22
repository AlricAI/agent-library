# Sprint4 Gui Checklist

> This checklist focuses on testing Sprint 4 features through the web interface at http://localhost:14100

---

## Pre-Demo Setup

### 1. Verify Service

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Sprint 4 Multi-Agent Coordination - GUI Manual Checklist

This checklist focuses on testing Sprint 4 features through the web interface at http://localhost:14100

---

## Pre-Demo Setup

### 1. Verify Services Running
- [ ] Open terminal and run: `pm2 list`
- [ ] Confirm both services show "online":
  - `codeframe-staging-backend` (port 14200)
  - `codeframe-staging-frontend` (port 14100)
- [ ] If not running: `pm2 restart all`

### 2. Open Frontend
- [ ] Open browser to: http://localhost:14100
- [ ] **Expected**: Status dashboard loads
- [ ] **Expected**: No console errors (press F12 to check)

---

## Phase 1: Project Setup

### Test 1.1: Create Demo Project
- [ ] Click **"Create Project"** or **"New Project"** button
- [ ] Enter project details:
  - **Name**: "Sprint 4 Multi-Agent Demo"
  - **Root Path**: `/tmp/sprint4-demo` (or leave default)
  - **Description**: "Testing multi-agent coordination"
- [ ] Click **"Create"** or **"Save"**
- [ ] **Expected**: Project appears in project list
- [ ] **Expected**: Project ID is assigned (note it for later)

### Test 1.2: Open Project View
- [ ] Click on the newly created project
- [ ] **Expected**: Project detail page loads
- [ ] **Expected**: See tabs or sections for:
  - Tasks
  - Issues (if applicable)
  - Agents (if visible)
  - Activity/Timeline

---

## Phase 2: Create Task Hierarchy with Dependencies

### Test 2.1: Create Independent Task (Foundation)
- [ ] Click **"Add Task"** or **"Create Task"**
- [ ] Fill in task details:
  - **Title**: "Setup Database Schema"
  - **Description**: "Initialize database tables and relationships"
  - **Status**: "completed" (mark as already done)
  - **Depends On**: (leave empty - no dependencies)
  - **Priority**: High (if available)
- [ ] Click **"Save"** or **"Create"**
- [ ] **Expected**: Task appears in task list
- [ ] **Expected**: Task shows "completed" status
- [ ] **Note**: Record Task ID (should be 1)

### Test 2.2: Create Parallel Frontend Task
- [ ] Create new task

*[truncated — see source for full prompt]*