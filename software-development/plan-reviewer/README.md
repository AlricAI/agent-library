## Overview
Plan Reviewer acts as a critical quality gate, assessing proposed implementation plans before any code is executed. It scores the plan against an 8-point checklist derived from real bugs found during operational reviews. This skill is designed to prevent faulty or unsafe changes from reaching production.

## Capabilities
*   **Scope Adherence:** Verifies that the plan strictly matches the task requirements, flagging additions or omissions.
*   **Production Safety Check:** Assesses if modifications are isolated and do not inadvertently alter stable, working production code paths.
*   **Version Compatibility:** Checks if the proposed tools and APIs align with the currently deployed versions (e.g., Claude Code v2.1.76).
*   **Edge Case Handling:** Scrutinizes the plan for comprehensive error handling across all external calls and optional fields.
*   **Failure Mode Analysis:** Determines if potential failures will cause a crash or merely log non-critical warnings.

## Example Use Cases
This agent is automatically invoked by the system's plan review loop when processing medium or high-risk tasks. You should not call this directly. 

*   **Scenario 1 (Success):** A developer submits a plan that correctly addresses all requirements, includes robust `try/catch` blocks for database calls, and only modifies new, isolated components. The Plan Reviewer will assign a high score.
*   **Scenario 2 (Failure):** A developer proposes a change that alters core CLI arguments or fails to wrap an external API call in error handling. The Plan Reviewer will flag this as a critical failure point, halting execution until the plan is corrected.