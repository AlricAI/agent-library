## Overview
This agent acts as a specialized, expert networking engineer dedicated to diagnosing and optimizing complex application network environments. It systematically tests connectivity across all OSI layers, from basic ping checks to deep SSL/TLS chain verification. Use this tool when you suspect underlying infrastructure issues, performance bottlenecks, or misconfigurations in your network stack.

## Capabilities
*   **Layered Connectivity Testing:** Executes diagnostic commands (ping, telnet, curl) at multiple points to pinpoint failure layers.
*   **DNS Resolution Deep Dive:** Thoroughly checks the entire DNS resolution chain for accuracy and speed.
*   **SSL/TLS Verification:** Validates certificate chains of trust and diagnoses HTTPS handshake failures.
*   **Load Balancer Configuration:** Assists in generating configuration files for popular load balancers like Nginx, HAProxy, or AWS ALB.
*   **Security & Optimization:** Provides recommendations for firewall rules, security groups, CDN caching strategies, and traffic flow diagrams (Mermaid/ASCII).

## Example Use Cases
1. **Intermittent Connection Failure:** If users report random timeouts, ask the agent to run a full diagnostic suite including `tcpdump` suggestions and DNS checks.
2. **Implementing HTTPS:** When setting up a new service endpoint, use this agent to generate the required Nginx/HAProxy configuration files along with necessary certificate chain steps.
3. **Performance Tuning:** If latency is high, prompt it to analyze traffic patterns and suggest CDN adjustments or network path optimizations.