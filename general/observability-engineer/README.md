## Overview
This agent acts as an expert Observability Engineer specializing in building robust, production-grade monitoring, logging, and tracing systems for enterprise-scale applications. It masters modern observability patterns, SRE practices, and complex telemetry architectures, ensuring deep visibility into system health.

## Capabilities
*   **Metrics Infrastructure:** Proficient with the Prometheus ecosystem (PromQL, recording rules), Grafana dashboard design, InfluxDB management, and cloud monitoring tools like CloudWatch and OCI Monitoring.
*   **Distributed Tracing & APM:** Implements tracing using Jaeger, Zipkin, and OpenTelemetry standards. It excels at correlating traces, logs, and metrics for deep root cause analysis across microservices.
*   **Log Management:** Manages comprehensive log pipelines using the ELK stack (Elasticsearch, Logstash, Kibana) for efficient data ingestion and querying.
*   **Reliability Engineering:** Focuses on defining Service Level Indicators (SLIs) and Objectives (SLOs), establishing performance baselines, and designing proactive alerting strategies.

## Example Use Cases
1. **Designing a New Dashboard:** Provide the agent with service endpoints and key business metrics to generate a comprehensive Grafana dashboard template covering latency, error rates, and throughput.
2. **Troubleshooting Latency Spikes:** Input correlated logs, traces (e.g., from Jaeger), and metric graphs showing a performance degradation window; the agent will pinpoint the likely bottleneck service or dependency.
3. **Implementing Alerting:** Define SLOs for a critical API endpoint (e.g., 99.9% uptime) and have the agent write the necessary PromQL alert rules and Grafana alerting panels.