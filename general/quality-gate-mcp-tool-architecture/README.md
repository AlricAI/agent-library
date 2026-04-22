# Quality Gate Mcp Tool Architecture

> **Design Document for SDK Migration Task 2.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Quality Gate MCP Tool Architecture
**Design Document for SDK Migration Task 2.4**

**Author**: System Architect (Claude Code)
**Date**: 2025-11-30
**Version**: 1.0
**Status**: DESIGN COMPLETE - Ready for Implementation
**Related**: [SDK Migration Plan](SDK_MIGRATION_IMPLEMENTATION_PLAN.md), Task 2.4

---

## Executive Summary

This document defines the architecture for exposing CodeFRAME's quality gates as an MCP tool, enabling Claude Agent SDK to invoke quality checks programmatically. The design prioritizes **thin wrapper approach** to minimize code duplication while providing a clean SDK-compatible interface.

### Key Decisions

| Decision | Choice | Rationale |
|----------|--------|-----------|
| **Location** | `codeframe/lib/quality_gate_tool.py` | Colocate with existing quality gate logic (not separate MCP module) |
| **Pattern** | Thin wrapper over `QualityGates` | Reuse 969 lines of existing, tested code |
| **SDK Integration** | Direct function callable | No MCP server boilerplate needed (in-process invocation) |
| **Database Dependency** | Pass database reference | Quality gates need DB for blocker creation, task status updates |
| **Error Handling** | Structured result format | Return errors as data, not exceptions |

---

## 1. Architecture Overview

### 1.1 Component Diagram

```
┌─────────────────────────────────────────────────────────────┐
│ Claude Agent SDK (ClaudeSDKClient)                          │
│ - Invokes quality_gate_tool via tool call                   │
└────────────────┬────────────────────────────────────────────┘
                 │
                 │ tool call: run_quality_gates(task_id, checks)
                 │
                 ▼
┌─────────────────────────────────────────────────────────────┐
│ codeframe/lib/quality_gate_tool.py (NEW)                    │
│ ┌─────────────────────────────────────────────────────────┐ │
│ │ async def run_quality_gates()                           │ │
│ │   - Validates parameters                      

*[truncated — see source for full prompt]*