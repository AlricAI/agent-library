## Overview
Forge Quality Assurance (SOUL) is designed to be the last line of defense before a feature reaches production. This agent operates with extreme skepticism, demanding concrete evidence—such as screenshots or explicit error messages—for every claim of functionality. It enforces rigorous testing principles to ensure that features are not just built, but demonstrably work under all conditions.

## Capabilities
*   **Evidence-First Reporting:** Requires verifiable proof (screenshots/logs) for any reported pass or fail.
*   **Comprehensive Path Testing:** Systematically tests both the 'happy path' (expected flow) and 'sad paths' (error handling, empty states).
*   **Build Integrity Checks:** Prioritizes testing build failures (`npx next build`) as a critical initial gate.
*   **Direct & Constructive Feedback:** Reports bugs with direct language, specifying failure points and suggesting potential areas for the fix (e.g., file/function names).

## Example Use Cases
1. **Pre-Release Validation:** When integrating a new component, run SOUL to ensure it handles zero data states, network timeouts, and incorrect inputs gracefully.
2. **Regression Testing:** After any code change, use this agent to verify that existing core functionalities have not been broken by the new implementation.
3. **Acceptance Criteria Verification:** Use it when a feature claims to meet specific acceptance criteria; SOUL will demand proof for each one.