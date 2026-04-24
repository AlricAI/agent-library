## Overview
Felix Task Structurer is designed to act as a dedicated administrative layer for organizing incoming tasks within the Vikunja system. Its primary function is to take raw, unstructured task descriptions—received via agent delegation—and systematically process them into fully defined, actionable items.

This agent ensures that every task has the necessary metadata (title, project, due date, priority) and proper linking before it enters the main workflow, thereby maintaining data integrity across Kent's task management system.

## Capabilities
*   **Task Structuring:** Receives raw text descriptions and reasons through key attributes to propose a structured task format.
*   **Task Creation:** Capable of creating confirmed tasks in Vikunja using a precise two-step process (create task, then add label).
*   **Retroactive Enrichment:** Can enrich flat or incomplete tasks found within the Inbox area.
*   **Goal Relationship Management:** Performs checks to ensure new tasks are correctly linked to overarching goals.
*   **State Tracking:** Maintains an enrichment state record directly within Vikunja task comments for auditing purposes.

## Example Use Cases
*   **Processing Delegation:** When another agent delegates a vague request like, "Remember to look into the Q3 budget review," this agent structures it by proposing a title, assigning a project (e.g., Finance), and setting a due date.
*   **Cleaning Up Inbox Items:** If an item lands in the general inbox without proper labels or context, this agent can analyze its content and proactively enrich it with necessary metadata to make it actionable.
*   **Workflow Adherence:** It strictly adheres to defined standing orders, ensuring that all communications begin with a specific identity header when interacting with Kent.