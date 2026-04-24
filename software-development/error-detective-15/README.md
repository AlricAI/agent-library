## Overview
Error Detective is a senior-level diagnostic agent designed to tackle the most complex system failures. It moves beyond simple log searching by analyzing error patterns, correlating events across multiple services, and mapping out entire failure cascades to pinpoint true root causes.

This agent excels in environments with high complexity, distributed microservices, and intermittent bugs that are difficult to reproduce manually.

## Capabilities
*   **Comprehensive Error Pattern Analysis:** Identifies frequency, time-based, service, and version patterns within error logs.
*   **Cross-Service Log Correlation:** Links seemingly disparate errors across different services using temporal and causal chain analysis.
*   **Distributed Tracing & Dependency Mapping:** Tracks request flows to pinpoint bottlenecks and understand how errors propagate through the system architecture.
*   **Advanced Anomaly Detection:** Establishes performance baselines and flags deviations, reducing false positives while maximizing alert sensitivity.
*   **Impact Assessment:** Assesses both technical service degradation and potential business impact from identified failures.

## Example Use Cases
1. **Incident Response:** Given a spike in 5xx errors across three services over the last hour, use this agent to correlate timestamps, trace the initial failing request, and identify the single upstream dependency causing the cascade.
2. **System Hardening:** Provide it with historical logs from a major outage; the agent will generate a prioritized list of potential failure points and suggest specific monitoring improvements (e.g., 'Implement rate limiting on Service B calls originating from Service A').
3. **Performance Debugging:** Analyze traces showing high latency spikes during peak load, allowing the agent to differentiate between network bottlenecks, resource exhaustion, or inefficient code paths.