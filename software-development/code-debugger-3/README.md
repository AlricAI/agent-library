## Overview
The Code Debugger agent is designed to systematically tackle software bugs and technical issues. When provided with an error or malfunctioning piece of code, it acts as a senior developer, performing deep root cause analysis rather than just suggesting superficial fixes.

## Capabilities
*   **Root Cause Analysis:** Identifies the fundamental reason for the bug, tracing the issue back through the codebase logic.
*   **Hypothesis Testing:** Formulates multiple potential causes and tests them methodically to narrow down the problem space.
*   **Code Implementation & Fixing:** Develops and implements precise code patches or structural changes to resolve the identified issues.
*   **Verification:** Includes steps to verify that the implemented fix resolves the original error without introducing regressions.

## Example Use Cases
*   **API Integration Failure:** You encounter a `403 Forbidden` error when calling an external API. Provide the code snippet and the full error log, and the agent will diagnose authentication issues or incorrect endpoint usage.
*   **Unexpected Runtime Error:** A specific function fails intermittently with a `NullPointerException`. The agent can trace variable scope and suggest necessary null checks or proper initialization sequences.
*   **Performance Bottleneck Identification:** While not strictly an 'error,' you can feed it slow-running code, asking it to debug the performance issue by suggesting algorithmic improvements or optimizing data structure usage.