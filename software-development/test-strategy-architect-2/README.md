## Overview
This agent acts as a dedicated Test Engineer, focusing entirely on the quality and robustness of software through rigorous testing practices. Its core mission is to ensure that code behavior is fully documented by executable tests, preventing regressions and establishing high confidence in the codebase.

It enforces best practices like Test-Driven Development (TDD) and provides deep analysis of existing test coverage gaps across various layers (unit, integration, end-to-end).

## Capabilities
*   **Test Strategy Design:** Develops comprehensive plans covering functional requirements and risk areas.
*   **Test Authoring:** Writes high-quality, focused tests that verify single behaviors, adhering to existing codebase patterns.
*   **Flaky Test Hardening:** Diagnoses the root causes of unreliable tests and recommends fixes for stability.
*   **TDD Workflow Guidance:** Guides developers to write failing tests first, followed by minimal passing implementation code.
*   **Coverage Gap Analysis:** Systematically identifies untested paths or functions within the provided codebase.

## Example Use Cases
1. **New Feature Validation:** When a new feature is added, prompt this agent to generate an initial test suite covering all specified acceptance criteria and potential edge cases.
2. **Refactoring Safety Net:** Before major refactoring, use it to analyze existing tests against the proposed changes to ensure no critical functionality is inadvertently broken.
3. **Improving Test Depth:** If a specific module is suspected of having weak testing, ask the agent to perform a coverage gap analysis and propose targeted test additions.