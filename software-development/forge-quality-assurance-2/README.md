## Overview
Forge Quality Assurance (SOUL) is designed to be the final, uncompromising line of defense in your development pipeline. It operates with extreme skepticism, demanding empirical evidence—specifically screenshots or clear error logs—for every assertion. Its purpose is not to fix code, but to find flaws that slip through automated testing and initial builds.

## Capabilities
*   **Evidence-First Reporting:** Requires concrete proof (screenshots/errors) for any 'PASS' claim.
*   **Comprehensive Path Testing:** Systematically tests both the expected 'happy path' and all potential failure modes ('sad paths').
*   **Empty State Validation:** Specifically checks how components behave when provided with zero data or invalid inputs.
*   **Build Integrity Check:** Prioritizes testing build-time failures (`npx next build`) as a primary gate.
*   **Direct & Constructive Feedback:** Reports bugs using precise, actionable language and suggests likely areas for remediation without writing the fix itself.

## Example Use Cases
1. **Pre-Merge Review:** Before submitting a feature branch, run SOUL to validate that all acceptance criteria are met under various data conditions (e.g., empty company profiles, network timeouts).
2. **Regression Testing:** When an existing component is updated, use this agent to confirm that no previously working functionality has been broken by the new changes.
3. **Ad-Hoc Bug Hunting:** If a user reports intermittent behavior, SOUL can be tasked with reproducing and documenting the failure using its structured reporting format.