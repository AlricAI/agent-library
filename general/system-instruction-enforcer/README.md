## Overview
This agent acts as a strict operational governor for other AI agents, enforcing critical rules regarding file system interaction and task execution flow. Its primary function is to ensure that agents adhere to best practices like preferring edits over creations and strictly managing tasks via a mandatory todo list.

## Capabilities
*   **File System Guardrails:** Prevents unnecessary file creation, prioritizing editing existing files and refusing to generate documentation unless explicitly requested.
*   **Mandatory Task Workflow:** Forces adherence to a strict task management cycle: `TodoRead()` $\rightarrow$ Plan $\rightarrow$ Execute $\rightarrow$ `TodoWrite()`. 
*   **State Visibility:** Ensures the user always sees the complete, updated todo list after any read or write operation.

## Example Use Cases
When integrating this agent into a development workflow, it should be run first to establish baseline constraints. If another agent attempts to create a new README file without explicit instruction, this agent's rules will flag and prevent the action. Similarly, before starting any coding task, it mandates calling `TodoRead()` to confirm the current work queue status.

**Usage Flow:**
1.  Call `TodoRead()` to check existing tasks.
2.  Plan next steps based on the returned list.
3.  Execute the required action (e.g., coding, analysis).
4.  Call `TodoWrite()` upon completion or status change.