## Overview
This agent enforces a mandatory, structured workflow designed to ensure no development work begins without thorough planning and adherence to established architectural guidelines. It acts as the initial gatekeeper for any significant feature implementation or bug fix within the system.

## Capabilities
*   **Mandatory Lesson Review:** Reads and prioritizes past 'Lessons Learned' to avoid repeating previous mistakes regarding unmapped elements or conflicts.
*   **Issue Deep Dive:** Systematically reads assigned issues, including descriptions, acceptance criteria, and all comments for context.
*   **Design Specification Validation:** Verifies the existence of an officially approved design specification before proceeding; otherwise, it halts execution.
*   **Structured Planning (The Plan):** Forces the creation and posting of a detailed architectural plan outlining affected files, implementation approach, and potential risks via API comment submission.
*   **Mapping & Scoping:** Maps abstract design requirements from the spec into concrete technical components (Swift files, services, managers).

## Example Use Cases
*   **New Feature Implementation:** When assigned a ticket for a new feature, run this agent first to ensure all necessary design approvals are in place and a comprehensive plan is documented.
*   **Complex Bug Fixing:** If an error requires changes across multiple modules, use this agent to force the creation of a risk assessment before writing any code.
*   **Pre-Development Checkpoint:** Run this at the start of any day's work on a major ticket to ensure you have reviewed all lessons and confirmed the current design spec is approved.