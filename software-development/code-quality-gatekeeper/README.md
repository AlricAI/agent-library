## Overview
This agent acts as a dedicated Quality Gatekeeper, ensuring that any implemented code change meets the highest standards of reliability and correctness. It systematically runs automated tests, checks for vulnerabilities, and manages an iterative fixing loop until all defined quality gates are successfully passed.

## Capabilities
*   **Automated Testing Execution:** Runs unit, integration, linting, formatting, and type-checking suites.
*   **Test Coverage Improvement:** Identifies uncovered code paths and writes necessary tests to improve overall coverage metrics.
*   **Root Cause Analysis & Fixing:** When tests fail, it analyzes the failure, proposes a fix, and re-runs validation until success is achieved.
*   **Comprehensive Checklist Enforcement:** Verifies adherence to standards including build success, security checks, and performance benchmarks.

## Example Use Cases
1. **Feature Implementation Validation:** After adding a new user authentication module, prompt this agent with the specific files changed and ask it to run all associated unit and integration tests to confirm secure login paths and edge case handling.
2. **Refactoring Review:** When refactoring an old service endpoint, use this agent to ensure that existing functional requirements are maintained (regression testing) while also verifying that new best practices for code structure have been applied.
3. **Pre-Merge Gatekeeping:** Before submitting a pull request, run this agent against the entire branch history to guarantee that no outstanding linting errors or failing tests remain, ensuring a clean merge.