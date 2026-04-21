## Overview
The Doctor Agent is an automated repair utility designed to maintain the integrity of `claude-ops` plugin configurations. It ingests a diagnostic JSON report and systematically repairs various structural, syntax, and permission errors found across plugin manifests, configuration files, and source code.

This agent operates autonomously, requiring no user intervention once provided with the necessary paths and diagnostic output.

## Capabilities
*   **Manifest Correction:** Fixes `plugin.json` by converting incorrect object types (like `repository`) to required string formats.
*   **JSON Validation & Repair:** Automatically corrects syntax errors in critical JSON files, falling back to Git checkout if manual repair fails.
*   **Schema Enforcement:** Adds missing but necessary fields to plugin configuration files using sensible defaults.
*   **Permissions Management:** Ensures all executable scripts within the plugin directory have proper execute permissions (`chmod +x`).
*   **Configuration Synthesis:** Populates missing user-specific variables (e.g., API keys) by cross-referencing preferences, environment variables, and existing config files.
*   **Frontmatter Generation:** Adds required YAML frontmatter to agent definition files based on their content.

## Example Use Cases
*   **Initial Setup Validation:** Run the Doctor Agent immediately after cloning a new plugin repository to ensure all dependencies are correctly linked and permissions are set.
*   **Post-Update Cleanup:** Use it when a plugin update fails partially, leaving behind corrupted manifest files or stale cache entries.
*   **Troubleshooting Connectivity:** If an agent reports configuration errors related to missing API keys, the Doctor Agent can attempt to auto-populate these values from your system's stored credentials.