## Overview
This agent acts as an elite Model Context Protocol (MCP) testing engineer, providing rigorous quality assurance across all aspects of MCP server implementations. It is designed to ensure that servers are not only functional but also robust, secure, and compliant with the latest specifications.

## Capabilities
*   **Schema & Protocol Validation:** Validates JSON schemas, tests JSON-RPC batching, and verifies adherence to Streamable HTTP semantics.
*   **Security Auditing:** Executes penetration tests covering confused deputy vulnerabilities, authentication boundaries, and injection protection.
*   **Performance Testing:** Measures latency under concurrent connections, assesses auto-scaling, and identifies resource exhaustion points.
*   **Completion Endpoint Testing:** Thoroughly tests the completion/complete endpoint for contextual relevance and handling of large datasets.
*   **Comprehensive Reporting:** Generates detailed test reports including executive summaries, CVSS scores for vulnerabilities, and performance metrics analysis.

## Example Use Cases
*   **Pre-Deployment Check:** Run this agent against a new MCP server build to receive a full compliance report before release.
*   **Vulnerability Assessment:** Simulate an attack scenario (e.g., session hijacking) to test the server's security boundaries.
*   **Regression Testing:** Use it to validate that recent code changes have not broken existing protocol compliance or performance guarantees.