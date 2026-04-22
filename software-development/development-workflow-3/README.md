# Development Workflow

> description: | Defines the standard development workflow, including the mandatory file analysis protocol, smart development patterns, and the prioritization of specialized MCP tools to ensure code quality, consistency, and efficiency. alwaysApply: true

## Tags
`typescript`

## System Prompt
---
description: |
  Defines the standard development workflow, including the mandatory file analysis protocol, smart development patterns, and the prioritization of specialized MCP tools to ensure code quality, consistency, and efficiency.
alwaysApply: true
priority: 2
---

# Development Workflow

This document outlines the mandatory workflow for all development tasks. It ensures that every action is preceded by proper analysis, follows established patterns, and utilizes the most effective tools available.

## 1. Mandatory Protocol: Analyze Before Action

**This is the most critical rule in the workflow. It is not optional.**

**NEVER** read, modify, or work with any file without **FIRST** running `analyze_file`. This is a non-negotiable safety and quality protocol.

### 1.1. The Analysis Workflow
1.  **Analyze the File:** Before any operation, run `analyze_file` to get a comprehensive overview.
    ```json
    {
      "tool": "analyze_file",
      "args": { "filePath": "/path/to/your/file.ts", "includeErrors": true }
    }
    ```
2.  **Assess Health:** Check the `health_summary.overall_status`.
    *   `"healthy"`: ✅ Safe to proceed.
    *   `"has_warnings"`: ⚠️ Proceed with caution.
    *   `"needs_attention"`: ❌ **STOP.** You MUST fix the TypeScript errors before making any other changes.
3.  **Understand Context:** Review the file's structure, imports, and exports to understand its role in the system.
4.  **Store Insights:** After analysis, store key findings in the memory system to accelerate future work.

### 1.2. Post-Modification Verification
After every modification, you **MUST** re-run `analyze_file` to verify that no new errors have been introduced and that the file's health has been maintained or improved.

## 2. Tool Prioritization: Use Specialized Tools

To ensure accuracy, context-awareness, and knowledge retention, you **MUST** prioritize specialized MCP Server tools over generic alternatives.

### Tool Selection Hierarchy
| Task | ✅ ALWAYS USE (Pr

*[truncated — see source for full prompt]*