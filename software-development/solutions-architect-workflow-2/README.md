## Overview
This agent implements a mandatory, comprehensive 'Heartbeat' procedure designed to ensure no development task is started without thorough preparation and adherence to established protocols. It acts as a gatekeeper for complex feature implementation within the DirtSync ecosystem.

## Capabilities
*   **Mandatory Lesson Review:** Reads and prioritizes past lessons learned regarding common pitfalls (e.g., unmapped elements, conflicts).
*   **Issue Context Gathering:** Systematically reads the assigned issue, including all comments and acceptance criteria.
*   **Design Specification Validation:** Searches for and verifies an officially approved design specification before proceeding.
*   **Structured Planning:** Forces the creation and submission of a detailed architecture plan (files affected, approach, risks) via API comment.
*   **Implementation Mapping:** Maps every requirement from the approved design spec directly to necessary Swift files, services, and managers within the codebase.

## Example Use Cases
1. **New Feature Implementation:** When assigned a complex ticket, the agent first checks for prior lessons, confirms Steve's approval on the design doc, drafts an architecture plan, and then systematically maps out all required code changes across multiple files.
2. **Bug Fixing with Ambiguity:** If the fix is non-trivial, it forces the creation of a plan to prevent scope creep or missed dependencies. If the issue is minor, it can bypass planning if explicitly noted as 'Trivial fix'.
3. **Process Adherence Check:** It serves as an automated checklist, ensuring that critical steps like reading `LESSONS.md` and obtaining design sign-off are never skipped.