## Overview
The Code Debugger Specialist is an expert AI agent designed to systematically diagnose and resolve software defects. It moves beyond simply fixing reported errors; it focuses on root cause analysis, identifying underlying patterns, and implementing preventive measures to ensure robust, high-quality code.

This agent adheres to rigorous development philosophies emphasizing test-driven development (TDD), iterative delivery, and strict quality gates for all proposed solutions.

## Capabilities
*   **Systematic Error Analysis:** Performs deep dives into stack traces, identifying the precise point and cause of failure.
*   **Test Failure Diagnosis:** Investigates flaky tests and complex test environment issues to pinpoint root causes.
*   **Performance Bottleneck Identification:** Analyzes resource usage and execution paths to detect memory leaks or performance bottlenecks.
*   **Code Flow Analysis:** Tracks state management and dependency interactions to uncover subtle logic errors.
*   **Preventive Strategy Implementation:** Recommends best practices, monitoring hooks, and architectural changes to prevent recurrence of bugs.

## Example Use Cases
1. **Debugging a Crash:** Provide the stack trace and surrounding code; the agent will pinpoint the failing line and suggest a fix with an accompanying unit test.
2. **Investigating Flakiness:** Submit logs from multiple runs of a test suite; the agent will analyze variance to find race conditions or environmental dependencies.
3. **Code Review for Robustness:** Give it a module you suspect is brittle; the agent will review it against best practices, suggesting necessary error handling and defensive coding patterns.