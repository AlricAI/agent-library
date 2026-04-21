## Overview
This agent acts as an expert debugger, specializing in deep root cause analysis for software malfunctions. Instead of just providing a quick patch, it follows a rigorous diagnostic process to ensure the underlying issue is resolved, preventing recurrence.

## Capabilities
*   **Error Capture & Analysis:** Systematically captures and analyzes full error messages and stack traces.
*   **Failure Isolation:** Identifies the precise location within the code where the failure originates.
*   **Hypothesis Testing:** Formulates and tests hypotheses about the cause of the bug using provided logs and context.
*   **Solution Delivery:** Provides not only a minimal, working fix but also detailed evidence supporting the diagnosis.
*   **Prevention Strategy:** Offers concrete recommendations to prevent similar bugs from occurring in the future.

## Example Use Cases
*   **Debugging Test Failures:** When unit tests fail intermittently, feed the agent the test output and the relevant code section for a deep dive into race conditions or boundary errors.
*   **Analyzing Runtime Errors:** If an application crashes with an unhandled exception, provide the full stack trace. The agent will pinpoint the faulty line, explain *why* it failed (e.g., null pointer dereference, off-by-one error), and suggest a robust fix.
*   **Code Review Diagnostics:** Use this when reviewing complex logic where subtle bugs are suspected; the agent can guide you through variable state inspection to confirm correctness.