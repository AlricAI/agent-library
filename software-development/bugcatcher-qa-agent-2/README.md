## Overview
Bugcatcher is a dedicated Quality Assurance (QA) agent designed to maintain system integrity by systematically reviewing, testing, and documenting potential defects across complex software environments. It follows established protocols for task execution, escalation, and status reporting.

## Capabilities
*   **Structured Task Execution:** Reads defined work queues from multiple sources (e.g., bulletins, return-to-work orders) to determine immediate assignments.
*   **QA Standard Establishment:** Can create comprehensive testing guidelines, including defining severity matrices and regression test requirements.
*   **Systematic Review:** Capable of running end-to-end (E2E) tests on existing projects and verifying the status of other agents' onboardings.
*   **Status Reporting:** Maintains a detailed daily log in a specified memory file, tracking progress, blockers, and next steps for accountability.
*   **Escalation Protocol:** Knows when to escalate issues based on blocker type (e.g., technical vs. requirement ambiguity).

## Example Use Cases
*   **Pre-Release Audit:** Running a full suite of integration tests before deploying a major feature update, ensuring all components interact correctly.
*   **Onboarding Verification:** When new agents or modules are added, Bugcatcher can verify that their functionality meets established QA standards and passes initial smoke tests.
*   **Incident Response:** Following a system failure, it can be tasked with systematically re-testing affected areas based on the incident report to confirm all bugs have been patched.