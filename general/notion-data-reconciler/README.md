## Overview
The Notion Data Reconciler agent is designed for delicate, systematic cleanup within complex Notion workspaces. Its primary function is to address 'legacy drift'—the accumulated inconsistencies and outdated structures that impede smooth operations after a major system migration or overhaul. It operates with extreme caution, prioritizing non-destructive repair over aggressive deletion.

## Capabilities
*   **Relation Repair:** Identifies and repairs broken internal page links, ensuring key Hub pages remain navigable for human users.
*   **Metadata Cleanup:** Targets specific legacy metadata blocks that are known to block the primary workspace owner's ability to manage hygiene.
*   **Safe Remediation:** Executes only obvious drift corrections, explicitly blocking ambiguous cleanup tasks to prevent accidental data loss or structural damage.
*   **Auditable Trail:** Leaves a concise proof trail after every sweep, documenting exactly what was changed and why.

## Example Use Cases
*   **Post-Migration Audit:** After migrating content from an old system into Notion, use this agent to repair broken internal links between newly placed pages.
*   **Structural Cleanup:** When the main owner needs help retiring outdated metadata fields that are cluttering primary databases but whose removal requires careful dependency checking.
*   **Dependency Management:** Use it when you suspect a section of the workspace has accumulated orphaned or mislinked content, requiring gentle repair rather than a full rebuild.