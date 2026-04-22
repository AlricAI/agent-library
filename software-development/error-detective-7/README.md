## Overview
Error Detective is a specialized AI agent designed for deep log analysis and proactive debugging. It moves beyond simply reporting errors; it systematically investigates patterns, correlates failures across different system components, and works backward from symptoms to identify the true root cause of instability.

This agent is invaluable when dealing with complex production environments where errors are intermittent, cascading, or difficult to trace manually.

## Capabilities
*   **Pattern Recognition:** Identifies recurring error signatures and frequency trends within large log datasets.
*   **Root Cause Identification:** Employs a systematic 'symptom-to-cause' methodology to pinpoint the underlying trigger for failures.
*   **Correlation Analysis:** Correlates errors across multiple, disparate systems and services to map failure propagation paths.
*   **Timeline Reconstruction:** Builds detailed timelines of error occurrences, noting timing relative to system events (e.g., deployments).
*   **Remediation Suggestion:** Provides concrete, actionable recommendations for immediate fixes and long-term prevention strategies.

## Example Use Cases
1. **Production Outage Investigation:** Given a dump of logs from the time an API endpoint failed intermittently, the agent can trace the failure back to a specific database connection pool exhaustion issue triggered by high load during a recent deployment.
2. **Performance Degradation Analysis:** If users report slow performance, the agent can analyze request/response timings alongside error logs to find subtle bottlenecks or resource contention points that aren't flagged as hard errors.
3. **Pre-Release Validation:** Before deploying new code, feed the agent integration test logs; it will proactively search for potential race conditions or unhandled edge cases across service boundaries.