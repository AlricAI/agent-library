## Overview
This agent acts as a comprehensive maintenance routine for Notion workspaces, designed to prevent 'workspace drift' by systematically auditing and repairing structural inconsistencies. It moves beyond simple content updates to enforce data governance across linked pages, ensuring that the knowledge base remains reliable, deduplicated, and easily navigable for its users.

## Capabilities
*   **Deterministic Key Verification:** Prioritizes verifying natural keys first, followed by placement, metadata, and formatting checks to ensure structural integrity before any content modification. 
*   **Routine Reconciliation Sweep:** Inspects newly created or modified pages in Work Queue, Knowledge, and Skills databases to deduplicate safe duplicates and repair critical fields (owner, related-work, canonical-source, etc.).
*   **Stale Page Auditing:** Runs daily checks for knowledge pages that are overdue for review or lack necessary metadata (like an owner), escalating them if they cannot be safely refreshed.
*   **Structural Integrity Sweep:** Conducts weekly inspections of the entire Blueprint Hub structure to identify orphaned pages, broken relations, and database misplacements.
*   **Drift Detection:** Monitors for systemic issues, such as multiple agents creating redundant artifacts or ownership conflicts between different tracking systems (e.g., Work Queue vs. Paperclip).

## Example Use Cases
*   **Onboarding New Content:** When a new project artifact is created, run this agent to ensure its metadata fields are correctly populated and linked to existing canonical sources.
*   **Quarterly Knowledge Audit:** Schedule this agent weekly or monthly to proactively find pages that haven't been touched or reviewed according to their defined cadence, preventing knowledge decay.
*   **Post-Migration Cleanup:** After integrating a new data source into Notion, use this agent to run a full reconciliation sweep to map and repair all related fields and deduplicate any overlapping entries.