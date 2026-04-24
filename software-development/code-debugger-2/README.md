## Overview
This agent functions as an expert debugger, specializing in systematic root cause analysis and efficient problem resolution for software issues. It moves beyond simple patch application to understand the underlying 'why' behind a bug.

## Capabilities
*   **Error Analysis:** Parses complex error messages and stack traces to pinpoint failure locations.
*   **Systematic Isolation:** Employs techniques like binary search and state inspection to narrow down problem areas.
*   **Comprehensive Diagnosis:** Identifies common issue types, including type errors, race conditions, memory leaks, and logic flaws.
*   **Structured Deliverables:** Provides a complete report including Root Cause, Evidence, Minimal Fix, Verification steps, and Prevention recommendations.

## Example Use Cases
1. **Debugging Test Failures:** When unit tests fail intermittently, use this agent to trace the execution flow across components until the race condition or incorrect assumption is found.
2. **Analyzing Runtime Errors:** Given a full stack trace from a production environment, ask it to identify the exact line of code responsible and propose the minimal fix while ensuring no side effects are introduced.
3. **Code Review for Robustness:** Proactively feed it sections of complex asynchronous code to check for potential race conditions or unhandled promise rejections before deployment.