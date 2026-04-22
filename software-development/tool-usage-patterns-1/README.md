# Tool Usage Patterns

> description: | Provides practical workflows for using specialized MCP tools. This rule covers the code investigation protocol for debugging and understanding code, and the memory management protocol for persistent knowledge capture and retrieval. alwaysApply: true

## Tags
`typescript`

## System Prompt
---
description: |
  Provides practical workflows for using specialized MCP tools. This rule covers the code investigation protocol for debugging and understanding code, and the memory management protocol for persistent knowledge capture and retrieval.
alwaysApply: true
---

# Tool Usage Patterns

This document provides standardized patterns for using specialized tools to investigate code and manage the project's knowledge base.

## 1. Code Investigation Protocol

This protocol should be followed whenever you encounter TypeScript errors, unknown APIs, or need to understand the implementation of a specific part of the codebase.

### When to Investigate
- **TypeScript Errors:** "Property does not exist," "Cannot find name," etc.
- **Import Errors:** "Module not found," "Export does not exist."
- **API Understanding:** Learning how a new library or internal module works.
- **Debugging:** Tracing unexpected behavior.

### Investigation Workflow
The investigation process is a funnel, moving from broad discovery to deep analysis.

1.  **Locate the Symbol (`find_implementation`):** This is your starting point. When you encounter an unknown symbol, use this tool to find where it's defined.
    ```json
    {
      "tool": "find_implementation",
      "args": { "symbol": "symbolName", "filePath": "path/to/current/file.ts" }
    }
    ```

2.  **Analyze the Source (`explore_source`):** Once you have the file path from `find_implementation`, use this tool to get a deep understanding of the source code, especially for code in `node_modules`.
    ```json
    {
      "tool": "explore_source",
      "args": { "filePath": "/path/to/implementation.ts", "symbol": "symbolName" }
    }
    ```

3.  **Trace Complex Dependencies (`trace_dependency_chain`):** If an import is complex (e.g., re-exported through multiple files), use this tool to map the entire chain back to its origin.
    ```json
    {
      "tool": "trace_dependency_chain",
      "args": { "symbol": "symbolName", "startFile

*[truncated — see source for full prompt]*