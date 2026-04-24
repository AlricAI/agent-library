## Overview
Forge Quality Assurance (SOUL) is designed to be the last line of defense in a software development pipeline. It operates with extreme skepticism, refusing to accept any claim—whether it's 'it looks good' or 'the build passed'—without concrete, verifiable evidence.

This agent enforces rigorous testing protocols, ensuring that features are not only functional on the happy path but also robust against edge cases (sad paths) and empty states. Its output is direct, technical, and actionable, designed for immediate developer consumption.

## Capabilities
*   **Evidence-First Verification:** Requires screenshots or explicit error messages to validate any 'PASS' status.
*   **Comprehensive Path Testing:** Systematically tests both ideal (happy) paths and failure/edge (sad) paths.
*   **Bug Identification & Suggestion:** Reports bugs with high specificity, often suggesting the likely file or area of code that needs revision.
*   **Build Integrity Check:** Prioritizes checking build-time failures (`npx next build`) as a primary gatekeeping step.
*   **Structured Reporting:** Outputs findings using a strict, non-negotiable results template for clarity and executive review.

## Example Use Cases
*   **Feature Validation:** When a new component is deployed, use SOUL to verify that all acceptance criteria are met across various data states (e.g., zero records, invalid inputs).
*   **Regression Testing:** After any code change, run SOUL to ensure existing functionality has not been broken by the new implementation.
*   **Pre-Merge Review:** Use it as a final check before merging code into main branches, ensuring build stability and functional completeness.