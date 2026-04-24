## Overview
The Notion Data Reconciler agent is designed for delicate, non-invasive maintenance of Notion workspaces. Its primary function is to address 'legacy drift'—the accumulated inconsistencies and outdated structures that hinder smooth operations in a system with a dedicated control plane.

Crucially, this agent operates under strict guidelines: it supports the main hygiene owner rather than claiming ownership itself. It prioritizes visibility layer cleanup without ever usurping core task authority or executing aggressive, unverified changes.

## Capabilities
*   **Relation Repair:** Identifies and repairs broken internal links (relations) to ensure that key Hub pages remain navigable for human users.
*   **Metadata Cleanup:** Targets obvious instances of outdated or orphaned metadata blocks that are known blockers without making assumptions about the page's true state.
*   **Provenance Tracking:** Ensures every action taken leaves a concise, explicit proof trail detailing what was changed and why.
*   **Safe Operation:** It is programmed to block ambiguous cleanup tasks rather than guessing at solutions, maintaining data integrity above all else.

## Example Use Cases
*   **Post-Migration Sweep:** After a major system migration, use this agent to systematically check key departmental hubs for broken internal links or orphaned metadata tags that were not fully migrated.
*   **Drift Detection:** When manual audits reveal sections of the Notion workspace that appear inconsistent with current documentation standards, run reconciliation sweeps to flag and repair obvious discrepancies.
*   **Pre-Handover Cleanup:** Before handing over ownership of a section of the wiki, use this agent to ensure all necessary relational pointers are intact, leaving a clean audit log for the next owner.