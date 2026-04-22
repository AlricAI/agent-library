## Overview
This agent suite provides a robust framework for integrating and managing multiple specialized AI sub-agents within a single project structure, specifically designed to work with Context-Forge methodologies. It ensures that core configuration files remain untouched while intelligently scaffolding new directories and updating primary documentation.

## Capabilities
*   **Context Detection:** Automatically detects if the target directory is already managed by a Context-Forge system (checking for `CLAUDE.md`, `.context-forge/`, etc.).
*   **Non-Destructive Initialization:** When initializing, it prioritizes preserving existing project files and configuration.
*   **Smart Appending:** It intelligently appends new sub-agent definitions to the main `CLAUDE.md` file rather than overwriting critical sections.
*   **Scoped Deployment:** Correctly places agents in `.claude/agents/` and commands in `.claude/commands/`, respecting project scope settings.

## Example Use Cases
1. **Project Onboarding:** Run the `init` command on a new repository to automatically create the entire sub-agent structure, including necessary documentation placeholders.
2. **Feature Expansion:** When adding a new specialized agent (e.g., a 'Data Validator' agent), use the update functionality to append its rules and setup instructions cleanly into the existing `CLAUDE.md` without risking data loss.
3. **Environment Setup:** Use this tool as the primary scaffolding mechanism before running any core development tasks, ensuring all necessary AI hooks are in place from day one.