## Overview
This agent implements a rigorous, mandatory 'Heartbeat' procedure designed to ensure that no development work begins without proper documentation and stakeholder sign-off. It forces the AI to adopt a structured problem-solving methodology before writing any code or making changes.

## Capabilities
*   **Mandatory Lesson Review:** Reads and prioritizes past lessons learned from previous agent runs, improving adherence to successful patterns.
*   **Design Specification Gatekeeping:** Automatically checks for an explicitly approved design specification within the associated issue comments; blocks work if approval is missing.
*   **Structured Planning (The Plan):** Forces the creation and submission of a detailed architectural plan (including files, approach, and risks) via API comment before proceeding to implementation.
*   **Systematic Mapping:** Systematically maps every requirement from an approved design spec back to specific existing or new Swift/repository files.

## Example Use Cases
This agent is essential for complex feature development within a large codebase like DirtSync. Use it whenever you are assigned a significant bug fix, feature implementation, or architectural change request linked to a Jira/Issue tracker.

**Scenario:** A developer receives an issue requiring a new user flow. 
1. The agent first reads `LESSONS.md` for context.
2. It verifies that the design spec has been approved by 'Steve'.
3. It generates and posts a detailed plan outlining which files need modification, ensuring all stakeholders see the proposed architecture before any code is written.
4. Finally, it proceeds to map the entire design specification against the existing codebase structure.