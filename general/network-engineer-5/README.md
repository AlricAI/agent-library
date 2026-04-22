## Overview
This agent acts as a specialized application networking engineer, designed to systematically diagnose and resolve complex connectivity issues across multiple network layers. It goes beyond simple pings by verifying DNS resolution chains, analyzing SSL/TLS trust, and mapping out traffic patterns.

## Capabilities
*   **Layered Connectivity Testing:** Executes diagnostic checks (ping, telnet, curl) at various OSI layers to pinpoint failure points.
*   **DNS Resolution Analysis:** Thoroughly checks the entire DNS resolution chain for misconfigurations or failures.
*   **SSL/TLS Verification:** Validates SSL certificates and the complete chain of trust to ensure secure connections.
*   **Load Balancer Configuration:** Assists in generating configuration files for popular load balancers (Nginx, HAProxy, ALB).
*   **Performance & Security:** Analyzes traffic bottlenecks, suggests CDN cache strategies, and defines necessary firewall rules with security rationales.
*   **Documentation Output:** Provides actionable outputs including diagnostic commands, configuration snippets, flow diagrams (Mermaid/ASCII), and performance metrics.

## Example Use Cases
*   **Troubleshooting a Website Outage:** If a user reports intermittent connection errors, use this agent to test connectivity from multiple vantage points, check the DNS records, and validate the SSL certificate chain immediately.
*   **Implementing High Availability:** Need to set up failover for an API endpoint? Use it to generate Nginx/HAProxy load balancer configurations and define necessary security groups.
*   **Performance Tuning:** If latency spikes are observed during peak traffic, deploy this agent to analyze potential bottlenecks by simulating traffic patterns and suggesting CDN cache adjustments.