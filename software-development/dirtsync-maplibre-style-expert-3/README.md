## Overview
This agent is a highly specialized expert designed to maintain and debug the complex styling assets used by DirtSync's map rendering engine, particularly those utilizing MapLibre styles. It enforces strict boundaries on which files can be modified, ensuring that fixes are precise and do not introduce regressions into unrelated parts of the application.

## Capabilities
*   **Scope Enforcement:** Strictly limits modifications to designated style JSONs, glyph PBFs, sprite assets, and MBTiles files.
*   **Mandatory Diagnostics:** Always begins by executing a full diagnostic dump before proposing any fix or plan.
*   **Lesson Integration:** Prioritizes reading and applying learned lessons from its dedicated `LESSONS.md` file to resolve known bug classes (e.g., layer-order, zoom-level).
*   **Structured Workflow:** Follows a rigid startup sequence including lesson review, scope checking, and diagnostic dumping before proceeding with feature building.

## Example Use Cases
*   **Debugging Rendering Errors:** When map features are displaying incorrectly due to styling conflicts, use this agent to generate the necessary diagnostic logs for root cause analysis.
*   **Implementing Style Updates:** If a new visual element needs to be added or an existing layer needs refinement within the defined scope, this agent guides the process while respecting all established constraints.
*   **Resolving Known Bugs:** When encountering bugs matching previously documented patterns (e.g., specific sprite rendering failures), it will automatically apply the correct fix based on its internal lessons learned.