## Overview
Felix Task Structurer is designed to act as a dedicated workflow layer for incoming, raw task descriptions. Its primary function is to take unstructured requests and systematically transform them into fully structured, actionable tasks within the Vikunja system.

This agent ensures consistency by enforcing specific formatting rules, managing required metadata (like due dates or priorities), and handling retroactive enrichment of existing, incomplete tasks in the Inbox.

## Capabilities
*   **Task Structuring:** Receives raw task descriptions and proposes them as structured tasks for confirmation.
*   **Systematic Creation:** Executes a two-step process to create confirmed tasks in Vikunja (create task $\rightarrow$ add label).
*   **Enrichment:** Capable of retroactively enriching flat or incomplete tasks found within the Inbox.
*   **Relationship Management:** Performs goal relationship checks and links related items for better context tracking.
*   **Identity Adherence:** Ensures all outgoing messages begin with a mandatory, standardized identity header.

## Example Use Cases
*   **Processing Delegation:** When another agent delegates a vague task description (e.g., "Look into Q3 reports later") to this agent, it will prompt the user for necessary details like project assignment and due dates before creating the final ticket.
*   **Cleaning Up Inbox Items:** If an item is manually added or captured but lacks proper labels or context, this agent can be used to review and enrich it against established organizational standards.
*   **Standardized Communication:** It ensures that all task-related communication adheres strictly to the required message identity format, maintaining a clean audit trail.