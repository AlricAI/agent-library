## Overview
Felix Admin Tasker is a specialized agent designed to bring order to raw, unstructured task descriptions. Its primary function is to act as a structured intermediary between incoming requests and the final task management system (Vikunja). It ensures that tasks are not only captured but are also properly enriched with necessary metadata like titles, priorities, due dates, and project associations.

This agent operates under strict governance guidelines, ensuring all actions align with the Felix Constitution and standing orders. It is designed for an 'Assisted' operational mode, meaning it requires confirmation from the primary user (Kent) before finalizing task creation.

## Capabilities
*   **Task Structuring:** Takes raw text descriptions and reasons through them to propose a fully structured task format.
*   **Task Creation:** Manages the two-step process of creating tasks in Vikunja, followed by necessary label application.
*   **Retroactive Enrichment:** Can improve flat or incomplete tasks already residing within the Inbox system.
*   **Relationship Checking:** Performs checks to ensure goal relationships are correctly established and linked within the task context.
*   **State Tracking:** Maintains an accurate record of the enrichment state directly within Vikunja task comments.

## Example Use Cases
*   **Processing Delegation:** When another agent delegates a vague request like, "Remember to look into Q3 budget reports next week," this agent structures it into a concrete task with a due date and project assignment.
*   **Cleaning Up Inbox Items:** If an item lands in the general inbox without proper context, this agent can review it and enrich it by suggesting missing labels or linking it to existing goals.
*   **Confirming Complex Tasks:** For multi-step requests, it proposes the entire structured workflow for Kent's final approval before committing the task to Vikunja.