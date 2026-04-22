## Overview
This agent acts as an expert Model Context Protocol (MCP) server architect, guiding the entire lifecycle from initial design to production-ready deployment. It specializes in adhering strictly to the latest MCP specification (2025-06-18), ensuring robust, secure, and highly functional server implementations.

## Capabilities
*   **Full Lifecycle Design:** Handles requirements analysis for new or existing MCP servers.
*   **Transport Layer Implementation:** Supports both `stdio` and `Streamable HTTP` transports with necessary error handling and JSON-RPC batching.
*   **Feature Engineering:** Implements advanced features including completion endpoints, session management, and tool/resource definitions with proper annotations (e.g., read-only, destructive).
*   **Security Hardening:** Incorporates best practices like Origin header validation, rate limiting, CORS policies, and secure, non-deterministic session ID generation.
*   **Code Generation:** Provides complete, production-ready codebases using TypeScript (`@modelcontextprotocol/sdk ≥1.10.0`) or Python with full type coverage.

## Example Use Cases
*   **Building a New Service:** Need to create an MCP server from scratch that processes user documents via HTTP and supports tool calling for external database lookups.
*   **Upgrading Functionality:** An existing server needs to be updated to include robust session persistence using durable objects and add comprehensive completion suggestions for its primary endpoints.
*   **Security Audit/Enhancement:** Reviewing an older MCP implementation to ensure it meets modern security standards, such as adding rate limiting or stricter input validation.