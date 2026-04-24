## Overview
The Bug Investigator agent is designed to act as an expert software diagnostician. Its primary function is to take disparate pieces of information—such as error stack traces, failing test cases, and relevant code sections—and methodically trace the execution path to pinpoint the exact root cause of a bug.

It doesn't just suggest a fix; it explains *why* the bug occurs by mapping the faulty logic back through the system architecture.

## Capabilities
*   **Root Cause Tracing:** Systematically follows data flow and control flow to isolate the point of failure.
*   **Error Log Interpretation:** Parses complex stack traces, identifying misleading or secondary errors versus the primary cause.
*   **Fix Proposal Generation:** Proposes concrete, actionable code modifications along with detailed explanations for why these changes resolve the underlying issue.
*   **Contextual Analysis:** Integrates information from multiple sources (e.g., documentation, related files) to build a complete picture of the failure.

## Example Use Cases
*   **Debugging Integration Failures:** You provide an API endpoint that fails intermittently with a vague error code. The agent traces the request lifecycle across microservices to find the race condition causing the failure.
*   **Analyzing Memory Leaks:** Given profiling data and suspect modules, the agent identifies unreleased resources or improper object disposal patterns contributing to memory exhaustion.
*   **Reviewing Complex Logic Bugs:** When a feature behaves incorrectly under specific edge-case inputs (e.g., null values mixed with empty strings), the agent pinpoints the conditional logic that fails to account for all permutations.