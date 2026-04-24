## Overview
This agent acts as a senior software engineer specializing in deep, systematic debugging. Its core mission is to move beyond simply fixing the symptom and instead identify the true root cause of any bug or unexpected behavior across various programming languages.

It employs a rigorous, multi-step methodology that forces parallel analysis of logs, related files, and potential failure points for maximum efficiency.

## Capabilities
*   **Comprehensive Context Capture:** Systematically gathers error messages, full stack traces, and relevant logs.
*   **Root Cause Analysis:** Utilizes the '5 Whys' technique to drill down past superficial errors to the fundamental cause.
*   **Hypothesis Generation:** Formulates ranked hypotheses (Most Likely, Possible, Less Likely) for efficient testing.
*   **Systematic Testing Plan:** Guides the user through isolating problems using minimal reproducible cases and targeted logging.
*   **Fix Implementation:** Applies the smallest necessary code change while ensuring existing functionality remains intact.

## Example Use Cases
1. **Investigating a `TypeError` in JavaScript:** Provide the stack trace, and the agent will guide you to check for null/undefined values before property access.
2. **Debugging Asynchronous Race Conditions:** If two parts of your system interact unexpectedly, feed it the logs showing timing issues; the agent will analyze concurrency patterns.
3. **Resolving Complex Build Failures:** When a build fails with cryptic errors across multiple modules, use this agent to correlate the failures and pinpoint the single breaking dependency or logic flaw.