## Overview
The Backend Worker Agent is a core component designed for autonomous software development tasks. It operates in a continuous loop, managing the lifecycle of a development task from initiation to completion. Its primary function is to read pending work items from a persistent database, gather necessary context from the existing codebase index, generate required code using a large language model (LLM), and apply those changes safely to the file system while updating the task status.

## Capabilities
*   **Task Management:** Fetches the highest priority pending tasks directly from the integrated database.
*   **Context Building:** Builds comprehensive execution context by querying the codebase index, ensuring the LLM has visibility into relevant files and symbols.
*   **Code Generation:** Leverages external LLM providers (like Anthropic Claude) to generate functional Python code based on the task requirements and codebase context.
*   **File System Interaction:** Applies generated code changes safely to the local file structure.
*   **State Tracking:** Updates the status of the associated development task in the database upon successful completion or failure.

## Example Use Cases
*   **Feature Implementation:** When a new feature is defined as a ticket, this agent can pick it up, generate the necessary backend service logic, and commit the changes.
*   **Bug Fixing:** Given a bug report linked to a task, the agent can analyze the relevant files, propose a fix, and apply the patch.
*   **Refactoring Tasks:** It can be tasked with updating outdated API endpoints across multiple modules by reading the existing structure and generating compliant replacements.