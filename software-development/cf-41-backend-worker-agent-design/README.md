# CF 41 BACKEND WORKER AGENT DESIGN

> **Status**: Design Phase
**Priority**: P0
**Sprint**: 3 - Autonomous Agent Execution
**Estimated Effort**: 8-10 hours
**Author**: Claude Code (System 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CF-41: Backend Worker Agent - Design Specification

**Status**: Design Phase
**Priority**: P0
**Sprint**: 3 - Autonomous Agent Execution
**Estimated Effort**: 8-10 hours
**Author**: Claude Code (System Architect)
**Date**: 2025-10-17

---

## 1. Executive Summary

The Backend Worker Agent is the foundation of CodeFRAME's autonomous execution system. It reads tasks from the database, understands the codebase through indexing, writes Python code, runs tests, and self-corrects failures—all autonomously.

This agent bridges Sprint 2's planning capabilities (discovery, PRD, task decomposition) with Sprint 3's execution reality.

---

## 2. Requirements Analysis

### 2.1 Functional Requirements

**Primary Capabilities:**
1. **Task Retrieval**: Fetch pending tasks from database with priority ordering
2. **Context Building**: Use codebase indexing (cf-32) to understand code structure
3. **Code Generation**: Write Python code files using Anthropic Claude API
4. **File Operations**: Create/modify/delete files in project directory
5. **Test Integration**: Integrate with test runner (cf-42) for validation
6. **Self-Correction**: Fix failures up to 3 attempts (cf-43)
7. **Status Tracking**: Update task status in database throughout lifecycle

### 2.2 Non-Functional Requirements

**Quality:**
- 85%+ test coverage (TDD methodology)
- All public methods tested with RED-GREEN-REFACTOR
- Error handling for API failures, file I/O, database issues

**Performance:**
- Task execution latency: <60s for simple tasks
- Context retrieval: <5s (leverage cf-32 indexing)
- File writes: Atomic operations to prevent corruption

**Reliability:**
- Idempotent task execution (safe to retry)
- Transaction support for database updates
- Graceful degradation on API quota limits

---

## 3. System Architecture

### 3.1 Component Diagram

```
┌─────────────────────────────────────────────────────────────┐
│                    Backend Worker Agent                      │
├────────────────────────────────

*[truncated — see source for full prompt]*