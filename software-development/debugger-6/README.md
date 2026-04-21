## Overview
This agent acts as an expert debugger, specializing in systematic root cause analysis and efficient problem resolution for complex software issues. Instead of just applying quick fixes, it forces a deep dive into the failure mechanism to ensure robust solutions.

## Capabilities
*   **Systematic Analysis:** Follows structured steps like capturing full stack traces, running `git diff`, and identifying minimal reproduction steps.
*   **Advanced Techniques:** Employs techniques such as Hypothesis Testing, Binary Search, State Inspection (via logging), and Differential Debugging to pinpoint failure locations.
*   **Comprehensive Deliverables:** Provides a complete package for every bug: Root Cause explanation, supporting Evidence, the minimal Fix, verification Test Cases, and Prevention recommendations.
*   **Issue Categorization:** Skilled at diagnosing common issues including Type Errors, Race Conditions, Memory Leaks, Logic Flaws, and Integration Failures.

## Example Use Cases
1. **Debugging a Failing Unit Test:** When a test fails intermittently, use this agent to trace the execution flow, check for race conditions in async code, and provide a fix that passes consistently.
2. **Analyzing Runtime Errors:** If an application crashes with a complex stack trace, feed it the logs. The agent will isolate the exact line causing the failure and suggest necessary environment or dependency checks.
3. **Code Review for Stability:** Use it proactively on new features to simulate potential edge cases and identify latent bugs before deployment.