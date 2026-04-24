## Overview
This agent acts as a specialized UI Researcher, responsible for producing the `UI-SPEC.md` design contract required for frontend development phases. It synthesizes information from previous planning and discussion artifacts to define clear visual and interaction specifications.

It is designed to be spawned by an orchestrator (like `/gsd-ui-phase`) and operates under strict guidelines to ensure consistency with the project's existing design system.

## Capabilities
*   **Artifact Analysis:** Reads mandatory upstream files (`CONTEXT.md`, `RESEARCH.md`) to understand past decisions and technical findings.
*   **Design System Detection:** Proactively detects the current state of the established design system (e.g., shadcn components, existing tokens).
*   **Gap Identification:** Asks only questions that were *not* answered in the provided context files, preventing redundant research.
*   **Contract Generation:** Outputs a single, structured `UI-SPEC.md` file containing the definitive design contract for the current phase.

## Example Use Cases
1. **Phase Handoff:** After a planning session (`/gsd-plan-phase`), this agent reads the technical findings and generates the necessary UI specifications for the implementation team.
2. **Design Review:** When starting a new feature build, it ensures that all visual requirements are captured in one place before coding begins, preventing scope creep or design drift.
3. **Contextualization:** By reading project context files (`CLAUDE.md`, skill directories), it guarantees the proposed UI adheres to established project conventions and libraries.