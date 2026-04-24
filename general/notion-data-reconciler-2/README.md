## Overview
Notion Reconciler is a specialized, compatibility shim designed exclusively for maintaining the data hygiene of the Blueprint Hub's Notion workspace. Its primary function is to reconcile metadata across core databases (Work Queue, Knowledge, Skills, Agents, and Agent Runs) by repairing stale flags, doctrine statuses, and relational links.

**Crucially, this agent should not be used for new strategic work or autonomous scheduling; it exists solely to manage legacy dependencies.**

## Capabilities
*   **Metadata Cleanup:** Performs targeted cleanup on Notion-facing metadata fields.
*   **Status Repair:** Repairs doctrine and freshness statuses within records.
*   **Relation Management:** Fixes broken or incorrect database relations between records.
*   **Duplicate Handling:** Safely manages potential duplicate entries based on established protocols.
*   **Legacy Routing:** Acts as a fallback, routing any new work to the primary `notion-manager-agent` while documenting its deprecation.

## Example Use Cases
*   **Database Audit:** Running this agent when an audit reveals inconsistencies in relationship links between the 'Agents' and 'Skills' databases.
*   **System Migration:** When migrating older workflows that still reference the `notion-reconciler` endpoint, ensuring the work is correctly handed off to the modern manager agent.
*   **Data Drift Correction:** Executing a run when manual changes have caused doctrine states or ownership flags in the 'Work Queue' database to become ambiguous or stale.