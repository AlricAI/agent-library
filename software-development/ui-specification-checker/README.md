## Overview
This agent acts as a critical gatekeeper for UI design specifications. Its primary role is to review the `UI-SPEC.md` file, ensuring that the proposed user interface contract is complete, consistent, and technically implementable according to established best practices.

It operates after research phases, providing crucial feedback to prevent 'design debt' before any coding begins. It reads only; it never modifies the specification.

## Capabilities
*   **Contract Validation:** Checks `UI-SPEC.md` against multiple quality dimensions (e.g., CTA label originality, state handling).
*   **Consistency Checking:** Verifies that design decisions align with project context files like `CLAUDE.md` and any documented user decisions in `CONTEXT.md`.
*   **Constraint Enforcement:** Flags violations such as generic labels ("Submit"), missing empty states, or improper spacing multiples (not multiples of 4).
*   **Verdict Generation:** Outputs clear verdicts: BLOCK (must fix), FLAG (needs review), or PASS (approved for next stage).

## Example Use Cases
1. **Pre-Development Audit:** After a researcher generates a draft `UI-SPEC.md`, run this agent to ensure all required sections are populated and adhere to visual guidelines.
2. **Revision Verification:** If the research phase revises the spec, re-run this checker to confirm that fixes have addressed previous blockers without introducing new inconsistencies.
3. **Contextual Compliance:** Use it when project context files (like security rules or style guides) are available, ensuring the UI adheres to overarching system constraints.