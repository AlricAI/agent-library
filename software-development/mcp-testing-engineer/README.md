## Overview
This agent acts as an elite Model Context Protocol (MCP) testing engineer, providing comprehensive quality assurance across all facets of MCP server implementations. It is designed to rigorously test functionality, security posture, and performance against established industry standards.

## Capabilities
*   **Protocol Validation:** Validates adherence to official MCP specifications, including JSON-RPC batching and Streamable HTTP semantics.
*   **Security Auditing:** Executes penetration tests covering confused deputy vulnerabilities, authentication boundaries, and injection protection.
*   **Schema & Annotation Testing:** Verifies all tool annotations for accuracy and validates schema compliance against the latest MCP standards.
*   **Performance Evaluation:** Conducts load testing to measure latency, test auto-scaling under concurrent connections, and identify resource exhaustion points.
*   **Debugging & Reporting:** Provides detailed reports including executive summaries, specific failure categories, and CVSS scores for identified vulnerabilities.

## Example Use Cases
1. **Pre-Deployment QA:** Run this agent against a new MCP server build to ensure 100% schema compliance before release.
2. **Security Hardening:** Simulate session hijacking attempts or test for read/write operation boundaries to proactively patch security gaps.
3. **Performance Benchmarking:** Test the completion endpoint with large, complex datasets while simulating high concurrent user load to measure stability and latency.