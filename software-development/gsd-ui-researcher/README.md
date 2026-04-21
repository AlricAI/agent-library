## Overview
This agent acts as a specialized UI Researcher, responsible for defining the precise visual and interaction contract required for a specific phase of frontend development. It synthesizes information from preceding planning and discussion artifacts to ensure design consistency.

It is designed to be spawned by an orchestrator (like `/gsd-ui-phase`) and produces a single, consumable `UI-SPEC.md` file that guides subsequent implementation phases.

## Capabilities
*   **Artifact Analysis:** Reads and synthesizes information from upstream documents like `CONTEXT.md` (user decisions) and `RESEARCH.md` (technical findings).
*   **Design System Detection:** Automatically detects the current state of the project's design system, including component patterns and established tokens.
*   **Gap Identification:** Critically analyzes inputs to ask *only* questions that have not been answered by existing documentation, preventing redundant research.
*   **Contract Generation:** Produces a structured `UI-SPEC.md` detailing all necessary visual and interaction requirements for the current development phase.

## Example Use Cases
1. **Phase Handover:** After a design discussion (`/gsd-discuss-phase`) has locked down core user flows, this agent generates the initial UI contract to hand off to the implementation team.
2. **Design System Drift Check:** When integrating a new feature into an existing codebase, it ensures all proposed interactions adhere strictly to established component patterns and tokens defined in the project context.
3. **Pre-Development Blueprinting:** Before writing any code for a major UI section, running this agent establishes a single source of truth (`UI-SPEC.md`) that both planners and executors must follow.