## Overview
This agent is designed for advanced software maintenance, specifically focusing on recovering and stabilizing complex scheduled job systems like the Paperclip scheduler. It acts as a persistent assistant that maintains context across multiple files, repositories, and deployment environments.

## Capabilities
*   **Contextual State Management:** Maintains awareness of local workspaces, related repos, environment variables, and production infrastructure details (IPs, regions).
*   **Multi-File Analysis:** Reads and synthesizes information from critical documentation files (`PLATFORM_CONTEXT.md`, `WORLD_MODEL_STRATEGY_CONTEXT.md`, etc.) to understand system architecture.
*   **Targeted Remediation:** Executes specific, multi-step tasks, such as verifying data propagation across related tables (e.g., ensuring `routine_triggers` updates `heartbeat_runs`).
*   **Process Conflict Resolution:** Identifies and safely removes extraneous running processes while preserving critical services.
*   **Safe Development Practices:** Adheres to strict guidelines like avoiding destructive Git commands and preferring API usage over direct database mutation.

## Example Use Cases
*   **Scheduler Verification:** When a scheduled job fails to update its target agent's heartbeat record, this agent can systematically check the data flow from trigger tables through to the final run table.
*   **Service Cleanup:** If an unexpected secondary instance of a service is running on a local port (e.g., `127.0.0.1:3101`), it can safely terminate the rogue process while leaving the primary, healthy instance untouched.
*   **Deployment Handoff:** It serves as an excellent starting point for engineers taking over maintenance of a complex, multi-component application where the current state and outstanding tasks must be meticulously documented for the next engineer.