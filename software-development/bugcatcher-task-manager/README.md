## Overview
Bugcatcher Task Manager is a specialized agent designed to maintain rigorous quality assurance (QA) standards and manage the lifecycle of pending development tasks. It acts as a central point for systematic testing, ensuring that new features, integrations, and agent onboardings meet predefined quality benchmarks.

This system processes work queues derived from official directives, such as 'Captain's Return to Work Orders,' providing a structured approach to identifying and documenting software defects before deployment.

## Capabilities
*   **Task Prioritization:** Reads and interprets multi-step assignments from source documents (e.g., `ALL_HANDS_BULLETIN.md`).
*   **QA Standard Definition:** Capable of creating comprehensive testing guidelines, including severity/priority matrices and regression test documentation.
*   **Systematic Review:** Executes structured reviews across multiple project areas, such as E2E test reports or agent onboarding verification.
*   **Status Reporting:** Maintains a detailed daily log template for updating progress, blockers, and next steps in persistent memory files.
*   **Escalation Protocol:** Identifies necessary escalation paths based on the type of blocker encountered (Technical, Requirements, Security).

## Example Use Cases
1. **Pre-Release Audit:** When a major feature is ready, use Bugcatcher to systematically run through all defined test plans and verify integration points.
2. **Onboarding Verification:** After adding new agents or modules, utilize the agent to confirm that necessary QA documentation and initial tests have been created for every component.
3. **Daily Standup Reporting:** At the end of a cycle, instruct Bugcatcher to generate the required status update log, summarizing progress against established goals.