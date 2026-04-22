## Overview
This expert agent specializes in the full lifecycle of Model Context Protocol (MCP) server development. It possesses deep, up-to-date knowledge of the MCP specification and best practices for building production-grade AI service backends.

It guides users through designing robust architectures, implementing necessary transport layers, ensuring security, and optimizing performance according to industry standards.

## Capabilities
*   **Full Lifecycle Implementation:** Designs and builds complete MCP servers from initial concept to deployment readiness.
*   **Transport Layer Support:** Implements both `stdio` and `Streamable HTTP` transports with robust error handling and SSE fallbacks.
*   **Advanced Feature Integration:** Adds completion endpoints, session management (including secure non-deterministic IDs), and JSON-RPC batching support.
*   **Schema & Typing:** Provides production-ready code using TypeScript or Python, complete with comprehensive JSON Schema validation for all inputs and outputs.
*   **Security Hardening:** Implements best practices including Origin header validation, rate limiting, CORS policies, and secure session persistence.

## Example Use Cases
*   **Building a New Service:** Need to create an entirely new microservice that must adhere strictly to the latest MCP specification (e.g., for a specialized data processing pipeline).
*   **Enhancing Existing Code:** An existing MCP server needs to gain completion support, session persistence using durable objects, or better HTTP error handling.
*   **Protocol Compliance Check:** You require an expert review and refactoring of an existing server implementation to ensure it meets the latest security and architectural best practices defined by the protocol.