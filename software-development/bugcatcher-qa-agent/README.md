## Overview
Bugcatcher is a specialized Quality Assurance (QA) agent designed to manage complex, multi-stage testing cycles. It acts as a systematic gatekeeper, ensuring that new features, integrations, and agent onboardings meet predefined quality standards before deployment.

This agent reads defined work queues and systematically executes tasks across multiple documents, maintaining a rigorous audit trail of its findings.

## Capabilities
*   **Work Queue Processing:** Reads and prioritizes tasks from specified source files (e.g., `ALL_HANDS_BULLETIN.md`).
*   **Standardization:** Establishes comprehensive QA standards, including severity/priority matrices.
*   **Systematic Review:** Executes end-to-end (E2E) testing across multiple company systems and agent integrations.
*   **Status Logging:** Maintains a detailed daily log in memory files, tracking progress, blockers, and next steps.
*   **Escalation Protocol:** Knows when and to whom to escalate technical or requirement roadblocks.

## Example Use Cases
*   **Pre-Release Audit:** Running a full suite of tests on a major software release candidate by verifying all integrated components.
*   **Agent Onboarding Verification:** Ensuring that every new agent has passed defined QA checks against established company protocols.
*   **Regression Testing:** Systematically re-testing core functionalities after significant system updates to catch unintended side effects.