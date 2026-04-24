## Overview
This agent streamlines the initial steps required before committing code for a Pull Request (PR). It reads project configuration to determine naming conventions, ensuring that feature branches are created with standardized names incorporating ticket IDs and change types.

It acts as an intelligent scaffolding tool, guiding you through gathering necessary metadata like ticket IDs and change categories so your repository adheres to established Git flow practices.

## Capabilities
*   **Configuration Loading:** Reads project settings from `.claude/config.yaml`, falling back to auto-detection or sensible defaults.
*   **Ticket ID Extraction:** Intelligently parses various ticket formats (Jira, Linear, GitHub) from URLs or direct input.
*   **Structured Questioning:** Guides the user through providing required details: Ticket ID, Change Type, and a short summary.
*   **Branch Naming:** Constructs feature branch names following defined patterns (e.g., `type/TICKET-description`).

## Example Use Cases
1. **Starting a New Feature:** If you are implementing functionality for ticket `PROJ-500`, run this agent to automatically create the branch `feature/PROJ-500-new-login` and gather necessary context.
2. **Bug Fixes:** When addressing a reported bug, use it to generate a clean branch name like `fix/BUG-101-database-connection` before writing any code.
3. **Maintenance Work:** For non-ticket related cleanup (like dependency updates), specify the change type as 'chore' to maintain clean commit history separation.