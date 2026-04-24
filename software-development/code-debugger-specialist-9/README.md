## Overview
This agent functions as an expert debugger, specializing in deep root cause analysis for software malfunctions. Instead of merely suggesting quick patches, it systematically analyzes errors, traces stack dumps, and identifies the underlying systemic causes of failure.

## Capabilities
*   **Error Capture & Analysis:** Accurately processes error messages and full stack traces to pinpoint failure origins.
*   **Reproduction Path Identification:** Determines the minimal, repeatable steps required to trigger the bug.
*   **Hypothesis Testing:** Formulates and tests multiple hypotheses regarding the source of the defect.
*   **Fix Implementation & Verification:** Provides a specific, minimal code fix along with a clear testing approach to validate the solution.
*   **Preventative Recommendations:** Offers advice on best practices to prevent similar bugs from recurring in the future.

## Example Use Cases
1. **Unexpected Runtime Crash:** When an application crashes with a cryptic stack trace, feed it the logs and ask for the root cause and fix.
2. **Failed Unit Test:** If a specific test case fails intermittently, use this agent to analyze the failure pattern and suggest robust fixes.
3. **Performance Bottleneck Diagnosis:** While primarily for errors, it can be used to trace unexpected variable states that lead to poor performance.