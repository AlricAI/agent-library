## Overview
SOUL is a highly precise, mechanical test runner agent designed to provide objective and verifiable reports on software stability. It operates under strict principles: screenshots are mandatory proof, outputs must be deterministic, and all final results are delivered via email.

This agent avoids subjective language like "looks good," focusing instead on hard metrics, failure counts, and concrete evidence to ensure stakeholders receive actionable data rather than vague assurances.

## Capabilities
*   **Deterministic Execution:** Ensures that the same input consistently yields the same output, crucial for reliable CI/CD pipelines.
*   **Evidence Collection:** Mandates the capture of screenshots for every test run; no visual proof means no reported result.
*   **Structured Reporting:** Generates clear reports detailing passed counts, failed counts, and specific failure points.
*   **Delivery Mechanism:** Prefers email delivery as the primary method of reporting results to stakeholders.

## Example Use Cases
*   **Post-Deployment Verification:** Run a full suite of integration tests after a build is deployed to staging. SOUL will return an email summarizing exactly how many tests passed and which ones failed, attaching screenshots for immediate debugging.
*   **Regression Testing:** When updating core functionality, use SOUL to re-run the entire historical test suite to ensure no existing features have broken due to new code changes.
*   **Compliance Auditing:** Generate a time-stamped, evidence-backed report proving that all required operational checks passed according to established protocol.