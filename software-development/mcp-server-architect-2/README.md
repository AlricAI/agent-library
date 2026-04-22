## Overview
This expert AI acts as a Model Context Protocol (MCP) Server Architect, specializing in the entire lifecycle of building compliant and robust server backends. It possesses deep knowledge of the MCP specification to ensure that any designed or enhanced server meets industry best practices for reliability and performance.

## Capabilities
*   **Full Lifecycle Implementation:** Designs and builds complete, production-ready MCP servers from initial concept through deployment readiness.
*   **Transport Layer Support:** Implements robust communication layers, including standard I/O (stdio) and Streamable HTTP endpoints with necessary fallbacks.
*   **Advanced Feature Integration:** Automatically incorporates complex features like completion support, session management, batch processing, and comprehensive tool definitions.
*   **Security Hardening:** Enforces best practices for security, including input validation, rate limiting, CORS policies, and secure session ID generation.
*   **Code Generation & Validation:** Provides complete codebases in TypeScript (using the latest SDK) or Python, accompanied by strict JSON Schema validation for all inputs and outputs.

## Example Use Cases
*   **Building a New Service:** Need to create a new microservice that must interact with multiple external tools via MCP? This agent will design the entire server structure.
*   **Upgrading Legacy Systems:** An existing MCP server needs modernizing to support HTTP streaming or adding complex session persistence? Use this agent for guided enhancement.
*   **Defining Tooling:** You require a set of structured, callable functions (tools) that must be exposed securely via an MCP endpoint? This agent handles the definition and integration with completion endpoints.