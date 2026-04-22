# Database Repository Patterns

> description: SQLite database patterns and repository design for Project globs: - "packages/core-*/**/*.repo.ts"

## Tags
`typescript` `sqlite` `docker` `claude`

## System Prompt
---
description: SQLite database patterns and repository design for Project
globs:
  - "packages/core-*/**/*.repo.ts"
  - "packages/core-db/**/*"
  - "db/**/*.sql"
scopes:
  - database
  - sqlite
  - repository
  - project
alwaysApply: false
---

# Database Repository Patterns

## 🎯 Database Architecture

Project uses **SQLite** as the primary database for:
- **177 tracked projects** across Dev workspace
- **Motivation metrics** (quality scores, effort, features)
- **Session history** (todo tracking, accomplishments)
- **Health monitoring** (build status, test results)

**Location:** `/Users/dmieloch/Dev/.project/db/project.db`

**Why SQLite:**
- ✅ Single-file database (easy backup/restore)
- ✅ No server required (embedded)
- ✅ Fast for read-heavy workloads
- ✅ Perfect for desktop Electron apps
- ✅ ACID compliant (data integrity)

---

## 📐 Schema Structure (20+ Tables)

### Core Tables

```sql
-- Projects being tracked
CREATE TABLE projects (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  name TEXT NOT NULL UNIQUE,
  path TEXT NOT NULL UNIQUE,
  origin_type TEXT CHECK(origin_type IN ('created', 'forked', 'cloned')),
  ownership TEXT CHECK(ownership IN ('mine', 'customized-fork', 'exploring')),
  lifecycle TEXT CHECK(lifecycle IN ('using', 'building', 'paused', 'reference')),
  created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
  last_worked_on DATETIME,
  purpose TEXT,
  deployed_url TEXT
);

-- Quality and motivation metrics
CREATE TABLE quality_scores (
  project_id INTEGER PRIMARY KEY,
  quality_score INTEGER CHECK(quality_score BETWEEN 0 AND 100),
  test_coverage INTEGER,
  has_tests BOOLEAN,
  has_ci_cd BOOLEAN,
  has_brain_garden BOOLEAN,
  has_prd BOOLEAN,
  has_architecture_docs BOOLEAN,
  documentation_score INTEGER,
  calculated_at DATETIME DEFAULT CURRENT_TIMESTAMP,
  FOREIGN KEY (project_id) REFERENCES projects(id) ON DELETE CASCADE
);

-- Session tracking
CREATE TABLE claude_sessions (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  project_id INTEGER,
  session_id

*[truncated — see source for full prompt]*