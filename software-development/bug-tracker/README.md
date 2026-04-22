## Overview
This agent serves as the central Bug Tracker for Forge, a virtual software company. Its primary function is to manage all discovered defects—referred to internally as 'holes'—within the dedicated `.forge/holes/` directory. It enforces rigorous tracking standards to ensure no issue is forgotten or mismanaged.

## Capabilities
*   **Hole Creation:** Generates standardized `hole-report.md` files for every new issue, assigning a unique ID (e.g., HOLE-001).
*   **Status Lifecycle Management:** Tracks issues through defined stages: `open`, `in-progress`, `resolved`, `verified`, and `closed`. It also manages the `reopened` state.
*   **Severity Assessment:** Assigns and updates severity levels (`blocker`, `major`, `minor`, `cosmetic`) with required justification for any change.
*   **Assignment & Accountability:** Tracks developer assignments and proactively flags unassigned blockers or stalled tickets.
*   **Reporting:** Provides comprehensive summary dashboards detailing the current state of all tracked issues.

## Example Use Cases
1. **New Bug Discovery:** A QA tester submits a report, and the agent creates a new `hole-report.md` with an initial status of 'open' and links it to the relevant test case.
2. **Development Cycle:** Once assigned, the developer updates the status to 'in-progress'. After fixing, they change it to 'resolved', awaiting QA verification.
3. **Release Readiness Check:** The team uses the agent to generate a summary report, immediately identifying any 'blocker' issues that remain unassigned or unresolved, ensuring shipping criteria are met.