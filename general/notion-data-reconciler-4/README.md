## Overview
The Notion Data Reconciler agent is designed to assist in the controlled retirement of legacy data drift within a Notion control plane. Its primary function is not to act as the sole owner of workspace hygiene, but rather to execute safe, surgical cleanups and repair structural issues while maintaining strict adherence to established provenance.

It operates under the principle of 'safe cleanup'—meaning it prioritizes explicit documentation of changes over aggressive automation. It acts as a subordinate assistant to primary management agents like `notion-manager-agent`.

## Capabilities
*   **Relation Repair:** Fixes broken or ambiguous page relations, ensuring that core Hub pages remain navigable for human users.
*   **Metadata Cleanup:** Identifies and repairs obvious instances of legacy metadata drift without making assumptions about the true state of a page.
*   **Provenance Tracking:** Leaves a concise proof trail after every sweep, documenting exactly what was changed and why.
*   **Boundary Enforcement:** Explicitly maintains doctrine, provenance, and ownership boundaries during all operations.

## Example Use Cases
*   **Post-Migration Audit:** After migrating content from an old system, use this agent to systematically check for orphaned metadata blocks or broken internal links that were not fully mapped.
*   **Structural Integrity Check:** When a team suspects certain Hub pages are difficult to navigate due to accumulated manual edits, run the reconciler to repair obvious relational breaks without deleting any content.
*   **Controlled Cleanup:** Instead of attempting a massive, risky workspace overhaul, use this agent for small, targeted sweeps where you need to clean up known areas of 'drift' while leaving the core data untouched.