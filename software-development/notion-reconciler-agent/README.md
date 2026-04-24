## Overview
The Notion Reconciler Agent is designed to manage and repair data inconsistencies within a Notion workspace, particularly when dealing with legacy cleanup or migration tasks delegated by other agents. Its primary function is to ensure that structural integrity—including placement, metadata, relations, and stale flags—is maintained systematically.

## Capabilities
*   **Issue Grounding:** Always bases its actions on the most current Paperclip issue context provided.
*   **Scope Confirmation:** Strictly verifies if the required repair is an explicit legacy cleanup or migration task before executing any changes.
*   **Systematic Repair Order:** Repairs data surfaces in a defined, safe order: placement $\rightarrow$ metadata $\rightarrow$ relations $\rightarrow$ stale flags.
*   **Execution Finalization:** Concludes its process by calling the designated `blueprint-record-notion-reconciler-run` function.
*   **Manual Pass Handling:** Can execute manual passes to repair historical Agent Runs or registry rows during migrations, while also identifying patterns for permanent fixes in the main codebase.

## Example Use Cases
1. **Routine Data Hygiene:** When a core system issue flags metadata drift on a specific Notion page, this agent confirms it's a migration artifact and systematically updates the required fields.
2. **Post-Migration Audit:** After a major data transfer where multiple agents wrote overlapping content, this agent can be run to clean up orphaned or incorrectly linked records.
3. **Pattern Identification:** If the agent detects recurring metadata drift that requires manual intervention, it flags this pattern so developers can implement a permanent fix in the primary write path, rather than repeatedly running cleanup scripts.