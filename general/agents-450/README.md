# Agents

> **📝 SYNC RULE**: This file mirrors CLAUDE.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Atlas Project Context (Agent Version)

**📝 SYNC RULE**: This file mirrors CLAUDE.md for agent consistency.

## 🎯 Key Directives
- **Token Efficiency**: Use compact responses, abbreviations, and bullet points to conserve tokens.
- **Configuration Management**: All user-configurable values must be in `.env` and loaded via environment variables. Update `.env.template` with any new variables.
- **Component Registry**: Check `ATLAS_COMPONENT_INDEX.md` before creating new components to avoid duplication. Update the index when adding new capabilities.
- **DATABASE PATHS**: NEVER use hardcoded database paths. Always use `from helpers.database_config import get_database_path, get_database_connection`.

## 🤖 ARCHON MCP CONNECTION - CRITICAL SETUP

**PROBLEM**: Claude Code sessions lose MCP connection to Archon after restart. Tools like `mcp__archon__manage_task` become unavailable even when server is running.

**SOLUTION**:
1. **Verify Archon Running**: Check Docker containers are up
   ```bash
   docker ps | grep archon
   # Should show: archon-mcp (8051), archon-server (8181), archon-ui (5173)
   ```

2. **Add MCP Connection** (if not already done):
   ```bash
   claude mcp add --transport http archon http://localhost:8051/mcp
   ```

3. **Verify Connection**:
   ```bash
   claude mcp list
   # Should show: archon: http://localhost:8051/mcp (HTTP) - ✓ Connected
   ```

4. **CRITICAL**: **Restart Claude Code session** after adding MCP connection for tools to be available.

**Available Tools After Connection**:
- `mcp__archon__manage_task` - Get, create, update, list tasks
- `mcp__archon__manage_project` - Project management
- `mcp__archon__perform_rag_query` - Knowledge queries
- `mcp__archon__search_code_examples` - Code search
- `mcp__archon__get_available_sources` - List data sources

**Task Management Workflow**:
```bash
# Get current tasks
mcp__archon__manage_task(action="list")

# Get specific task
mcp__archon__manage_task(action="get", task_id="uuid-here")

# Upd

*[truncated — see source for full prompt]*