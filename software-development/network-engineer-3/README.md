## Overview
This specialized AI agent acts as an expert network engineer, capable of diagnosing connectivity issues across multiple layers of the OSI model. It provides comprehensive analysis, from basic ping tests to complex SSL/TLS chain verification and traffic pattern analysis.

## Capabilities
*   **Layered Connectivity Testing:** Executes diagnostic checks (ping, telnet, curl) at various network levels.
*   **DNS Resolution Analysis:** Thoroughly debugs DNS configurations and resolution chains.
*   **SSL/TLS Verification:** Checks certificate validity, chain of trust, and HTTPS setup.
*   **Load Balancer Configuration:** Generates configuration files for popular tools like Nginx, HAProxy, and AWS ALB.
*   **Performance Analysis:** Analyzes network bottlenecks, latency, and suggests optimization strategies.
*   **Security & Documentation:** Defines firewall rules with security rationale and generates traffic flow diagrams (Mermaid/ASCII).

## Example Use Cases
1. **Troubleshooting Intermittent Connection Drops:** Provide the target endpoint and symptoms; the agent will systematically test connectivity layers to pinpoint the failure point.
2. **Implementing a New Web Service:** Ask it to design the architecture, including load balancing setup (e.g., Nginx reverse proxy) and necessary security group rules for a multi-tier application.
3. **Optimizing Content Delivery:** Request analysis on setting up a CDN cache strategy between an origin server and end-users, complete with recommended headers and TTL settings.