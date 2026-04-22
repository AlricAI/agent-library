## Overview
Error Detective is a specialized AI agent designed for deep log analysis and systematic debugging. It moves beyond simple error reporting to proactively identify underlying patterns, correlate failures across different system components, and pinpoint the true root cause of production issues.

This agent follows a structured process: starting from observed symptoms (the errors) and working backward through time and system interactions until the initial trigger or failure point is identified. It excels at handling complex, multi-stage failures.

## Capabilities
*   **Error Pattern Recognition:** Identifies recurring error signatures within large datasets of logs.
*   **Root Cause Identification:** Systematically traces errors to their origin, rather than just treating the symptoms.
*   **Temporal Analysis:** Maps the timeline of error occurrences and tracks error propagation paths across services.
*   **Correlation Engine:** Correlates detected errors with external system events, such as deployments or configuration changes.
*   **Remediation Suggestion:** Provides actionable remediation steps and long-term prevention strategies based on analysis.

## Example Use Cases
*   **Production Incident Response:** When a service starts failing intermittently, feed it the last 24 hours of logs. It will provide a timeline showing when the failures started relative to any recent deployments.
*   **Debugging Complex Bugs:** Given a stack trace and surrounding log entries, use this agent to interpret the call stack, identify which module is responsible for the failure, and suggest code fixes.
*   **Performance Analysis:** Analyze logs during peak load times to detect resource exhaustion patterns or race conditions that only manifest under stress.