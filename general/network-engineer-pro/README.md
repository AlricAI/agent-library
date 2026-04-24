## Overview
This agent simulates a senior networking engineer, providing comprehensive diagnostic and configuration assistance for modern application networks. It systematically tests connectivity across all OSI layers, from basic ping checks to advanced SSL/TLS chain validation.

Whether you are debugging intermittent connection drops, optimizing latency between services, or setting up secure load balancing, this tool provides actionable commands, configuration snippets, and detailed analysis reports.

## Capabilities
*   **Layered Connectivity Testing:** Executes diagnostic steps like `ping`, `telnet`, and `curl` to pinpoint failure points. 
*   **DNS Resolution Analysis:** Thoroughly checks the entire DNS resolution chain for misconfigurations or failures.
*   **SSL/TLS Verification:** Validates certificate chains, expiration dates, and trust relationships for secure HTTPS endpoints.
*   **Load Balancer Configuration:** Generates configuration files for popular tools like Nginx, HAProxy, and AWS ALB.
*   **Performance Analysis:** Analyzes traffic patterns, identifies bottlenecks, and suggests optimization steps with relevant metrics.
*   **Security & Documentation:** Defines necessary firewall rules (with rationale) and generates flow diagrams using Mermaid or ASCII art.

## Example Use Cases
1. **Debugging a Web Service:** If users report intermittent 502 errors on an HTTPS endpoint, ask the agent to test connectivity from multiple vantage points, check the certificate chain, and review potential load balancer timeouts.
2. **Implementing High Availability:** Request configuration files for setting up an active-passive or active-active load balancing setup using Nginx across three different availability zones.
3. **Network Audit:** Provide a target hostname and ask the agent to perform a full network audit, covering DNS resolution, SSL validation, and suggesting necessary security group rules.