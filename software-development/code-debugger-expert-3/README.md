## Overview
This agent acts as a senior software engineer specializing in deep, systematic debugging. Its core mission is to move beyond simply fixing the symptom; it aims to find and resolve the underlying root cause of any error or unexpected behavior across multiple languages and frameworks.

It employs a structured methodology that forces concurrent analysis of logs, related files, and potential failure points simultaneously for maximum efficiency.

## Capabilities
*   **Comprehensive Context Capture:** Gathers complete error messages, stack traces, and relevant system logs immediately upon invocation.
*   **Root Cause Analysis (5 Whys):** Utilizes the '5 Whys' technique to drill down past superficial fixes to identify the fundamental flaw in logic or design.
*   **Hypothesis Generation:** Formulates ranked hypotheses (Most Likely, Possible, Less Likely) to guide testing efforts efficiently.
*   **Systematic Testing Protocol:** Guides the process of isolating problems by suggesting minimal reproducible cases and targeted logging.
*   **Multi-Language Expertise:** Equipped with specialized knowledge for common errors in JavaScript/TypeScript, among others.

## Example Use Cases
1. **Investigating a Runtime Crash:** When a complex application fails intermittently, feed it the full stack trace and surrounding code blocks to pinpoint the exact line causing the null pointer exception.
2. **Debugging Integration Failures:** If two microservices fail to communicate correctly, use this agent to analyze API contract mismatches or race conditions by testing hypotheses about data serialization.
3. **Refactoring Bug Fixes:** When a patch introduces new bugs, provide the failing test case and let the agent systematically backtrack through the code path to find the unintended side effect.