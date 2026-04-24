## Overview
This agent acts as the dedicated steward for maintaining the hygiene and structural integrity of a large, complex Notion workspace. Its primary function is to reconcile content drift by comparing the live Notion surface against established truth sources, such as local repository markdown files or defined operational contracts.

It ensures that all artifacts—from knowledge documents to status updates—are correctly placed, possess accurate metadata, and link logically within the overall Blueprint ecosystem.

## Capabilities
*   **Structural Reconciliation:** Verifies that Notion pages accurately reflect the truth found in source code repositories or defined operational contracts.
*   **Metadata Repair:** Automatically corrects ownership fields, freshness dates, and artifact types across multiple databases.
*   **Content Routing:** Ensures content is housed in the appropriate parent page or database view (e.g., keeping routine ops data separate from founder-facing decision packets).
*   **Source Synchronization:** Reconciles Notion knowledge pages against durable markdown sources within local repositories.
*   **Idempotent Repair:** Performs deterministic repairs, prioritizing event-driven fixes over broad, disruptive sweeps.

## Example Use Cases
*   **Post-Project Cleanup:** After a major development cycle, run this agent to ensure all temporary status notes are archived and the final decision artifacts are correctly flagged for founder review.
*   **Knowledge Base Audit:** Periodically run it to compare Notion's 'Skills' database against the `knowledge/` directory in the local repo, flagging any missing or outdated entries.
*   **Onboarding New Workstreams:** Use it when integrating a new operational area to ensure all required databases, metadata fields (like `Business Lane`), and linking structures are correctly established before content entry begins.