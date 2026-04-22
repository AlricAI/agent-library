## Overview
Forge is designed to be the single source of truth for any large, iterative software project. It enforces a structured directory layout within `.forge/` to meticulously track every aspect of development—from initial requirements and architectural decisions to execution plans, testing evidence, and final delivery reports.

This system ensures that no context, decision, or piece of work is lost, making it ideal for complex, multi-stage engineering efforts where traceability is paramount.

## Capabilities
*   **Structured State Persistence:** Maintains core project metadata (phase, progress) in `state.json` and runtime details in `runtime.json`.
*   **Lifecycle Artifact Management:** Organizes outputs by development phase (e.g., `design/`, `contracts/`, `plan.md`).
*   **Issue & Evidence Tracking:** Provides dedicated areas for issue logging (`holes/`) and verifiable claims (`evidence/`).
*   **Operational Logging:** Captures immutable records of activity via the append-only `events/` log.
*   **Context Snapshots:** Supports checkpointing through `checkpoints/` for session continuity.

## Example Use Cases
1. **Complex Feature Implementation:** When building a feature that requires sequential steps (e.g., Design $\rightarrow$ Contract $\rightarrow$ Implement $\rightarrow$ Test), Forge ensures the output of one phase is correctly ingested as input for the next.
2. **Auditing and Compliance:** Generating a complete, chronological report by reviewing `events/` and cross-referencing decisions in `design/` against final acceptance criteria in `tasks/`.
3. **Project Handoff:** Providing a new team member with a single directory structure that details the project's entire history, current blockers, and next steps.