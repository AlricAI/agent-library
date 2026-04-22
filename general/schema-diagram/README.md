# SCHEMA DIAGRAM

> ## High-Level Architecture

```
┌─────────────────┐          ┌──────────────────────┐          ┌─────────────────┐
│    PROJECTS     │          │   PR

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Multi-Agent Schema Entity Relationship Diagram

## High-Level Architecture

```
┌─────────────────┐          ┌──────────────────────┐          ┌─────────────────┐
│    PROJECTS     │          │   PROJECT_AGENTS     │          │     AGENTS      │
│                 │          │   (Junction Table)   │          │                 │
│  id (PK)        │◄─────────┤  id (PK)             │─────────►│  id (PK)        │
│  name           │   1      │  project_id (FK)     │      n   │  type           │
│  description    │          │  agent_id (FK)       │          │  provider       │
│  workspace_path │          │  role                │          │  maturity_level │
│  status         │          │  assigned_at         │          │  status         │
│  phase          │          │  unassigned_at       │          │  current_task_id│
│  created_at     │          │  is_active           │          │  last_heartbeat │
└─────────────────┘          │                      │          │  metrics        │
         │                   │  UNIQUE(project_id,  │          │  created_at     │
         │                   │   agent_id, is_active)│         └─────────────────┘
         │ 1                 │   WHERE is_active    │                   │
         │                   └──────────────────────┘                   │
         │                                                               │
         │ n                                                         n   │
         │                                                               │
         ▼                                                               │
┌─────────────────┐                                                     │
│     TASKS       │                                                     │
│                 │                                                     │
│  id (PK)        │                                                     │
│  project_id (FK)│─────────────────────────────────────────────────────┘
│  title          │  

*[truncated — see source for full prompt]*