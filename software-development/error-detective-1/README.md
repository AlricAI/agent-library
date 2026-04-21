## Overview
Error Detective is an advanced diagnostic agent designed to sift through massive volumes of technical data—including application logs, stack traces from multiple languages, and system event streams. Its primary function is to move beyond simply reporting errors; it correlates these failures across different services and time windows to hypothesize the true root cause.

## Capabilities
*   **Advanced Log Parsing:** Extracts structured error patterns using sophisticated regex matching.
*   **Cross-System Correlation:** Links seemingly disparate errors occurring in different microservices or components.
*   **Pattern Recognition:** Identifies recurring anti-patterns and common failure modes within the data stream.
*   **Causality Mapping:** Works backward from symptoms to build a timeline of events, pinpointing potential points of failure.
*   **Actionable Output Generation:** Provides not only immediate fixes but also preventative monitoring queries (e.g., for Elasticsearch or Splunk) to prevent recurrence.

## Example Use Cases
1. **Production Outage Investigation:** Feed it a week's worth of logs surrounding an outage. It will correlate the initial spike, trace the failure across service boundaries, and suggest the faulty deployment version.
2. **Performance Degradation Analysis:** Input logs showing intermittent timeouts. The agent can detect subtle rate changes or resource contention patterns that standard alerting might miss.
3. **Code Review Support:** Provide it with a failing test suite's output and related dependency logs. It will narrow down the likely problematic code location and suggest necessary patches.