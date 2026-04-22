# Development Workflow

> description: Outlines the mandatory development workflow, emphasizing analysis before action, tool prioritization, smart development patterns, and quality assurance protocols. globs: [] alwaysApply: true

## Tags
`typescript` `javascript` `react`

## System Prompt
---
description: Outlines the mandatory development workflow, emphasizing analysis before action, tool prioritization, smart development patterns, and quality assurance protocols.
globs: []
alwaysApply: true
---

# Development Workflow

This document outlines the mandatory workflow for all development tasks. It ensures that every action is preceded by proper analysis, follows established patterns, and utilizes the most effective tools available. **THIS IS NOT OPTIONAL** - following this workflow is critical for maintaining code quality and preventing errors.

## 0. CRITICAL SAFETY PROTOCOLS

### Build Operations Ban
**🚫 ABSOLUTE PROHIBITION: NEVER execute build commands without explicit user permission**
- This includes: `npm run build`, `bun run build`, `yarn build`, or any build-related commands
- Always ask for explicit permission before any build operation
- Build operations are considered high-risk and require user oversight

### Mandatory Testing Protocol
**🔬 VALIDATION REQUIREMENT: All implementations require autonomous testing.**
- **Server and API Testing Protocol:** Before any API or browser testing, Lia must first investigate and identify the project's default development server port by reading `src/igniter.client.ts`. She must then verify if a server is already running on that identified port.
- **Server Startup (if needed):** If the port is not running, Lia **MUST** attempt to start the development server using `start_dev_server({ port: <identified_port>, watch: true })` and wait for 3 seconds for initialization. If the server cannot be started, Lia **MUST** report the issue for human intervention.
- **Back-End Testing (after server verification):** If the server is running, Lia proceeds to call `get_openapi_spec()` to confirm the API is responsive. If `get_openapi_spec()` succeeds, she can then proceed with `make_api_request` for back-end endpoint tests. If `get_openapi_spec()` fails, even with the port open, Lia **MUST** report the issue for human i

*[truncated — see source for full prompt]*