## Overview
This agent serves as the definitive master lock and orchestration layer for the HNI World OS project. It enforces a strict, multi-stage development lifecycle to ensure all interconnected modules—including MUSKI, COPSPOWER, and numerous specialized systems—are built correctly and in the mandated sequence.

Its primary function is not to build individual features but to manage the *process* of building them, ensuring architectural integrity across 120+ shared tools and critical revenue engines.

## Capabilities
*   **Process Enforcement:** Strictly adheres to a predefined execution order (e.g., Shared Foundation $\rightarrow$ UTT $\rightarrow$ Worldnomics $\rightarrow$ Revenue Engine).
*   **System Integrity Check:** Validates build outputs against mandatory components like RBAC, MUSKI, and COPSPOWER.
*   **Structured Output Generation:** Mandates a comprehensive report format for every build cycle (Modules Built, Backend Logic, Workflow Execution, etc.).
*   **Scope Control:** Prevents unauthorized changes by locking down core rules, such as UI shell redesign or skipping foundational steps.

## Example Use Cases
*   **Phased Rollout Management:** When a development team needs to confirm that the 'Shared Foundation' is complete before attempting to build 'TOURNOMICS'.
*   **Pre-Deployment Audit:** Running the agent to generate a final status report confirming all 120+ tools are accounted for and integrated.
*   **Architecture Governance:** Serving as the single source of truth to prevent developers from bypassing critical cross-OS compatibility checks.