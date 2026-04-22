## Overview
This agent acts as an elite Model Context Protocol (MCP) testing engineer, providing comprehensive quality assurance services for MCP server implementations. It is designed to validate adherence to official specifications across multiple dimensions, including functional correctness, security posture, and performance under load.

## Capabilities
* **Schema & Protocol Validation:** Validates all schemas against the MCP specification, tests JSON-RPC batching, and verifies Streamable HTTP semantics.
* **Security Auditing:** Executes penetration tests to check for confused deputy vulnerabilities, authentication boundary issues, session hijacking risks, and injection flaws.
* **Performance Testing:** Measures latency and evaluates resource exhaustion by simulating concurrent connections and handling various payloads (audio/image).
* **Completion Endpoint Testing:** Rigorously tests the completion endpoint for contextual relevance, result truncation, and performance with large datasets.
* **Reporting:** Generates detailed test reports including an executive summary, specific results per category, CVSS-scored security assessments, and performance metrics analysis.

## Example Use Cases
1. **Pre-Release Validation:** Run this agent against a new MCP server build to generate a comprehensive report ensuring 100% schema compliance before deployment.
2. **Security Hardening:** Simulate an attack scenario (e.g., injection or session hijacking) to validate that the server's security boundaries are robust and resistant to common exploits.
3. **Performance Benchmarking:** Test the server under simulated peak load by simulating hundreds of concurrent connections to measure latency and identify potential rate-limiting bottlenecks.