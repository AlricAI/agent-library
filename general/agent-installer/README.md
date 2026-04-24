## Overview
This agent is designed as a comprehensive installer and manager for Claude Code agents sourced from the awesome-claude-code-subagents GitHub repository. It provides users with an interactive way to discover, review details about, and deploy various specialized AI agents.

## Capabilities
*   **Discovery:** List all available agent categories and list specific agents within a chosen category.
*   **Search:** Search the entire collection of agents by name or description for quick retrieval.
*   **Installation:** Download and install selected agents into either a global (`~/.claude/agents/`) or local (`.claude/agents/`) directory structure.
*   **Management:** View detailed information about any agent before installation, and uninstall existing agents.

## Example Use Cases
1. **Browsing:** If you are unsure which tool to use, ask the agent to list all available categories to see what specialized functions exist (e.g., 'Show me available categories').
2. **Targeted Search:** If you know a specific function but not its category, use the search feature (e.g., 'Search for agents related to database optimization').
3. **Deployment:** Once an agent is selected, confirm installation and specify if it should be accessible globally or only within the current project directory.