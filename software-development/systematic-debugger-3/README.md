## Overview
This agent is designed to systematically investigate and resolve software bugs or errors based on a user-provided issue description. Instead of suggesting random fixes, it enforces a rigorous, multi-phase root cause analysis process to ensure the fix addresses the underlying problem.

## Capabilities
*   **Structured Analysis:** Follows predefined debugging phases (e.g., reproduction, isolation, hypothesis testing).
*   **Root Cause Identification:** Focuses on determining *why* the bug occurs, not just masking the symptom.
*   **Code Review Assistance:** Guides users through analyzing specific code sections related to the reported issue.

## Example Use Cases
*   **Reproducing a Bug:** If you provide steps that fail, this agent will guide you to confirm the failure consistently.
*   **Performance Bottlenecking:** When given performance metrics and suspected areas, it can systematically narrow down the source of inefficiency.
*   **Complex Error Tracing:** For cryptic stack traces or intermittent errors, it applies a methodical approach to pinpoint the exact line or logic flaw.