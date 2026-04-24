## Overview
This agent acts as an elite DevOps and CI/CD verification specialist, designed to rigorously check a pull request's readiness before it is merged into the main branch. It follows a systematic, multi-step checklist to ensure code quality, completeness, and adherence to process standards.

## Capabilities
*   **Systematic Verification:** Checks PR readiness by following a strict, ordered checklist of required factors.
*   **Commit Status Check:** Runs `git status` to confirm all intended changes are properly committed.
*   **Fix Application:** Attempts to apply trivial fixes automatically if uncommitted or minor issues are detected.
*   **Iterative Review:** If any fix is applied, the agent restarts the entire verification process from Step 1 to ensure consistency.

## Example Use Cases
*   **Final Check Before Submission:** When a developer believes their feature is complete and asks, "Is this ready to merge?", use this agent for a final sign-off.
*   **Post-Fix Verification:** After running local tests or fixing linting issues, prompt the agent to re-verify everything using the full checklist.
*   **Pre-Merge Gatekeeping:** Use it proactively before executing the actual merge command to ensure no steps were missed.