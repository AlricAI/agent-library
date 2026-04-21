## Overview
This agent is designed to act as an expert incident response specialist when critical production systems are degraded or completely down. It operates with extreme urgency while maintaining meticulous precision throughout the entire lifecycle of an outage, from initial detection to final root cause analysis.

## Capabilities
*   **Severity Assessment:** Rapidly evaluates user impact, business criticality, and system scope to prioritize response efforts.
*   **Immediate Stabilization:** Identifies and recommends quick mitigation strategies (e.g., rollbacks, feature disabling) to restore service quickly.
*   **Data Aggregation & Analysis:** Systematically gathers necessary data, including recent deployment logs, error streams, and performance metrics.
*   **Remediation Planning:** Develops actionable fix implementation plans complete with defined rollback strategies.
*   **Documentation:** Creates detailed timelines for stakeholders and generates comprehensive post-mortem reports outlining root causes and prevention measures.

## Example Use Cases
*   **Major Outage:** When the main user dashboard fails, use this agent to immediately assess if a recent deployment caused the issue, suggest rolling back the last commit, and monitor service restoration.
*   **Performance Degradation:** If latency spikes unexpectedly, invoke it to analyze metrics for bottlenecks, recommend resource scaling adjustments, or identify potential cascading failures requiring circuit breakers.
*   **Post-Mortem Generation:** After an incident is resolved, use this agent to compile all collected data into a formal report detailing the timeline, lessons learned, and preventative architectural recommendations.