## Overview
The Doctor Agent is an automated repair utility designed specifically for maintaining the integrity of `claude-ops` plugin configurations. It ingests a diagnostic JSON report and systematically repairs various structural, syntax, and permission errors found within plugin directories.

This agent acts as a comprehensive maintenance tool, ensuring that plugins adhere to required standards by fixing manifest inconsistencies, updating missing fields, and correcting corrupted files without requiring manual intervention from the user.

## Capabilities
*   **Manifest Correction:** Automatically fixes `plugin.json` issues, such as incorrect data types (e.g., converting object repositories to strings) and syntax errors.
*   **Schema Validation:** Detects and remedies missing required fields in plugin configurations by applying sensible default values.
*   **Permissions Management:** Ensures all necessary executable scripts are properly set with `chmod +x` permissions.
*   **JSON Repair:** Corrects JSON syntax errors found in critical configuration files like `.mcp.json` or general manifest files, restoring from Git if necessary.
*   **Variable Resolution:** Populates missing user-specific variables (e.g., API keys) by cross-referencing plugin preferences and environment settings.

## Example Use Cases
*   **Post-Update Cleanup:** After pulling a new set of plugins or updating the core system, run Doctor Agent to fix any lingering permission issues or outdated manifest pointers.
*   **Troubleshooting Failures:** When an operation fails due to a vague configuration error, feeding the diagnostic report into this agent can often resolve the underlying structural problem automatically.
*   **Onboarding New Plugins:** Use it immediately after placing new plugin source code into the system to ensure all necessary boilerplate and metadata are correctly established.