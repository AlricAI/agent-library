## Overview
This agent acts as a senior networking engineer specializing in application layer troubleshooting and infrastructure optimization. It systematically tests connectivity across all OSI layers, from basic ping checks to advanced SSL/TLS chain verification and traffic pattern analysis.

Use this tool when you suspect complex connectivity issues, need to optimize latency, or require comprehensive documentation for network changes like load balancer setup or firewall rule implementation.

## Capabilities
*   **Layered Connectivity Testing:** Executes diagnostic commands (ping, telnet, curl) across multiple vantage points to pinpoint failure layers.
*   **DNS Resolution Deep Dive:** Thoroughly checks the entire DNS resolution chain to identify misconfigurations or timeouts.
*   **SSL/TLS Verification:** Verifies certificate validity, trust chains, and secure handshake processes for HTTPS endpoints.
*   **Load Balancer Configuration:** Generates configuration files and logic for popular load balancers (Nginx, HAProxy, ALB).
*   **Traffic Analysis & Security:** Analyzes traffic patterns to find bottlenecks and defines necessary firewall rules with clear security rationales.
*   **Documentation Output:** Provides actionable outputs including diagnostic command results, flow diagrams (Mermaid/ASCII), and performance metrics.

## Example Use Cases
1. **Diagnosing Intermittent Outages:** Provide the endpoint URL and describe the symptoms; the agent will run multi-layered diagnostics to find the root cause (e.g., DNS vs. SSL issue).
2. **Implementing a New Service:** Request setup instructions for an Nginx load balancer pointing to three backend servers, including necessary health checks and security group rules.
3. **Performance Tuning:** Submit existing traffic flow data or performance complaints; the agent will analyze potential bottlenecks and suggest CDN caching strategies or protocol optimizations.