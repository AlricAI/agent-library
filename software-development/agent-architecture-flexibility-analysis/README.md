# AGENT ARCHITECTURE FLEXIBILITY ANALYSIS

> **Date**: 2025-10-19
**Context**: Pre-Sprint 4 architectural review
**Concern**: Ensuring agent types aren't hard-coded and system supports future ext

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Architecture Flexibility Analysis
**Date**: 2025-10-19
**Context**: Pre-Sprint 4 architectural review
**Concern**: Ensuring agent types aren't hard-coded and system supports future extensibility

---

## Executive Summary

**CRITICAL FINDING**: The current architecture has **3 hard-coded constraints** that will block Claude Code skills integration and future agent type flexibility:

1. ✅ **Database schema CHECK constraint** (Line 103 of database.py) - Enum restricts agent types to 5 values
2. ✅ **CODEFRAME_SPEC.md documentation** (Lines 129-133) - Explicitly lists 4 agent types as "MVP"
3. ⚠️ **No plugin/skill discovery system** - cf-24.6 is planned but not implemented

**Risk Level**: 🔴 **HIGH** - Proceeding with Sprint 4 as currently specified will create technical debt

**Recommendation**: Refactor agent type system BEFORE implementing cf-21 (Frontend Agent) and cf-22 (Test Agent)

---

## Detailed Findings

### 1. Database Schema Constraint (CRITICAL)

**Location**: `codeframe/persistence/database.py:103`

```sql
CREATE TABLE IF NOT EXISTS agents (
    id TEXT PRIMARY KEY,
    type TEXT CHECK(type IN ('lead', 'backend', 'frontend', 'test', 'review')),
    provider TEXT,
    maturity_level TEXT CHECK(...),
    status TEXT CHECK(...),
    ...
)
```

**Problem**:
- Hard-coded enum: `'lead', 'backend', 'frontend', 'test', 'review'`
- Adding new agent types (e.g., "security", "accessibility", "docs") requires **schema migration**
- Claude Code skills cannot dynamically define new agent types
- Subagent spawning (cf-24.5) limited to these 5 types

**Impact**:
- ❌ **Blocks** Claude Code skills integration (cf-24.6)
- ❌ **Blocks** dynamic agent type creation
- ❌ **Forces** migration for every new agent capability
- ✅ **Allows** current 5 agent types to work

**Compatibility with Claude Code Skills**: 🔴 **INCOMPATIBLE**

---

### 2. Specification Documentation (MEDIUM)

**Location**: `CODEFRAME_SPEC.md:129-133`

```markdown
**Types** (MVP):
- **Backend Agent**:

*[truncated — see source for full prompt]*