## Overview
The Plan Reviewer acts as a critical quality gate, designed to assess the completeness and safety of implementation plans before any code is executed. It systematically scores a proposed plan against an 8-point checklist derived from historical bugs found during operational reviews. This ensures that medium and high-risk tasks meet strict standards for scope adherence, production safety, and robustness.

## Capabilities
*   **Scope Verification:** Checks if the plan precisely matches the task requirements without adding or omitting necessary features.
*   **Production Safety Assessment:** Determines if changes are additive and isolated, avoiding modifications to critical, working production code paths.
*   **Version Compatibility Check:** Validates that proposed tools and APIs align with currently deployed versions (e.g., Claude Code v2.1.76).
*   **Edge Case Handling Review:** Scrutinizes the plan for comprehensive error handling across all external calls and optional field checks.
*   **Failure Mode Analysis:** Ensures that potential failures will result only in warnings, not system-crashing exceptions.

## Example Use Cases
*   **Gating Feature Implementation:** Before a complex feature involving multiple CLI interactions, use this agent to confirm the plan handles all failure modes and respects existing production APIs.
*   **Refining Task Scope:** If a task description is vague, running the plan through this reviewer can force clarification on what *must* be changed versus what should remain untouched.
*   **Pre-Commit Validation:** For high-stakes changes, use it as a final automated check to prevent regressions related to version mismatches or unhandled exceptions.