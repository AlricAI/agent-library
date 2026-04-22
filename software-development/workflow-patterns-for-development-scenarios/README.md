# Workflow Patterns for Development Scenarios

> description: Provides comprehensive workflow patterns that integrate with MCP tools to handle common development scenarios systematically. globs: [] alwaysApply: true

## Tags
`typescript` `javascript`

## System Prompt
---
description: Provides comprehensive workflow patterns that integrate with MCP tools to handle common development scenarios systematically.
globs: []
alwaysApply: true
---

# Workflow Patterns for Development Scenarios

This rule provides comprehensive workflow patterns that integrate with MCP tools to handle common development scenarios systematically. Use these patterns when you encounter specific situations not fully covered by the base rules, ensuring consistent and efficient approaches across different complexity levels.

## 1. Code Investigation & Debugging Workflows

### 1.1 TypeScript Compilation Errors Pattern

**When to Use**: When encountering TypeScript compilation errors that prevent build/deployment.

**Workflow Sequence**:
```mermaid
graph TD
    A[TS Compilation Error] --> B{analyze_file - health check}
    B --> C{Health status?}
    C -->|needs_attention| D[Fix immediate errors first]
    C -->|healthy/has_warnings| E[find_implementation - locate error source]
    E --> F{Implementation found?}
    F -->|No| G[grep search with error pattern]
    F -->|Yes| H[explore_source - examine implementation]
    H --> I{Type issues?}
    I -->|Yes| J[Trace import chain with trace_dependency_chain]
    I -->|No| K[Check file dependencies and imports]
    J --> L[Fix root cause in source file]
    K --> M[Update file imports/exports]
    L --> N[Re-analyze file health]
    M --> N
    N --> O{Health improved?}
    O -->|Yes| P[Proceed with development]
    O -->|No| Q[Store as bug_pattern memory]
    Q --> R[Escalate to human developer]
```

**Tool Chain**:
- `analyze_file` (MANDATORY - first step)
- `find_implementation` → `explore_source` → `trace_dependency_chain`
- `grep` (for complex pattern searches)
- `store_memory` (document solutions as `bug_pattern`)

**Success Criteria**:
- File health status changes from `needs_attention` to `healthy`
- No TypeScript compilation errors
- Solution documented for future reference

### 1.2 Runtime Error Resolution 

*[truncated — see source for full prompt]*