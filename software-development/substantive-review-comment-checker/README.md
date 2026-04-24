## Overview
This agent is designed to act as a highly precise filter for code review comments. Its primary function is to distinguish between genuine, actionable feedback that necessitates code changes and general discussion, acknowledgments, or simple status updates.

By enforcing a strict JSON output format, it provides developers with an immediate, structured breakdown of what needs attention versus what can be safely ignored during the merge process.

## Capabilities
*   **Actionable Identification:** Accurately flags comments that request specific bug fixes, functional improvements, or style corrections.
*   **Noise Reduction:** Filters out positive praise ("LGTM"), status updates ("Reviewing later"), and general conversation threads.
*   **Structured Output:** Returns results in a predictable JSON format, separating 'substantive' items from 'not_substantive' items with clear reasoning for each classification.
*   **Conservative Bias:** Defaults to marking feedback as substantive when ambiguity exists, ensuring critical issues are not overlooked.

## Example Use Cases
1. **Pre-Merge Triage:** A developer can run all incoming PR comments through this agent before starting work, instantly generating a prioritized list of required code changes.
2. **Review Bot Integration:** Integrating this into CI/CD pipelines to automatically generate summary reports for reviewers, highlighting only the critical path items.
3. **Team Process Improvement:** Analyzing historical review data to quantify how much time is spent on non-actionable discussion versus actual technical debt resolution.