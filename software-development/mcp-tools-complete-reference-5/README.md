# MCP Tools Complete Reference

> description: Complete reference for all MCP tools: CLI operations, API validation, documentation lookup, GitHub integration, file analysis, code investigation, memory management, task management. Use when: planning features, developing code, researching solutions, managing project knowledge, analyzi

## Tags
`typescript` `react` `nextjs` `docker` `claude`

## System Prompt
---
description: Complete reference for all MCP tools: CLI operations, API validation, documentation lookup, GitHub integration, file analysis, code investigation, memory management, task management. Use when: planning features, developing code, researching solutions, managing project knowledge, analyzing files, debugging issues.
globs: []
alwaysApply: true
---

# MCP Tools Complete Reference

## Tool Categories & Workflow Integration

### CLI & Project Management
Core project development lifecycle and scaffolding tools.

**`dev`** - Start Igniter.js development server
- **Description**: Starts the development server, enabling live reloading, client generation, and interactive debugging.
- **Parameters**: `port?: number`, `watch?: boolean`
- **Use when**: Beginning development sessions to run the project locally and test changes in real-time.
- **Workflow**: Start of Work phase.
- **Example**: `dev({ port: 3000, watch: true })`

**`build`** - Build the Igniter.js project
- **Description**: Compiles the project for production, including the web framework and the final Igniter.js client.
- **Parameters**: `mode?: "development" | "production"`
- **Use when**: Preparing for deployment or testing the production build locally.
- **Workflow**: Pre-deployment validation.
- **Example**: `build({ mode: "production" })`

**`test`** - Run project test suite
- **Description**: Executes the project's test suite to validate changes and prevent regressions.
- **Parameters**: `filter?: string`, `watch?: boolean`
- **Use when**: After making changes to ensure code quality and correctness.
- **Workflow**: Work phase validation, continuous testing.
- **Example**: `test({ filter: "@igniter-js/core", watch: false })`

**`generateFeature`** - Scaffold a new feature module
- **Description**: Creates a new, fully structured feature module with directories for controllers, procedures, and types.
- **Parameters**: `name: string`, `schema?: string`
- **Use when**: Starting a new area of functi

*[truncated — see source for full prompt]*