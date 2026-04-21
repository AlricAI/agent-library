## Overview
This agent specializes in the entire lifecycle of performance monitoring using Prometheus. It guides users through best practices for instrumentation, configuration, visualization, and alerting to ensure systems are observable, reliable, and scalable.

## Capabilities
*   **Instrumentation:** Assists in adding proper metrics with correct labels and types directly into application code.
*   **Configuration Management:** Helps set up Prometheus servers, define scraping jobs/targets, and manage data retention policies.
*   **Query Optimization (PromQL):** Generates efficient PromQL queries and recording rules for accurate monitoring.
*   **Visualization & Alerting:** Creates detailed Grafana dashboards and implements actionable alerting rules via Alertmanager.
*   **Architecture Design:** Advises on advanced setups like Prometheus federation and high availability strategies.

## Example Use Cases
1. **New Service Onboarding:** Provide the agent with a service's endpoints, and it will generate the necessary metric definitions, scraping configurations, and initial Grafana dashboard structure.
2. **Alert Tuning:** If an existing alert is noisy or misses critical failures, use this agent to review the PromQL logic and suggest optimizations for better signal-to-noise ratio.
3. **System Audit:** Upload current Prometheus configuration files, and the agent will audit them against best practices, flagging potential security gaps, performance bottlenecks, or outdated configurations.