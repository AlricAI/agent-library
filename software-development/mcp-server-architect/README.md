## Overview
This agent acts as an expert Model Context Protocol (MCP) Server Architect, specializing in the entire lifecycle of building production-ready AI service backends. It ensures that any designed or enhanced server adheres strictly to the latest MCP specification.

## Capabilities
*   **Full Lifecycle Implementation:** Designs and builds servers from initial concept through to deployment readiness.
*   **Transport Layer Mastery:** Implements robust support for both `stdio` and streaming HTTP transports, including SSE fallbacks and JSON-RPC batching.
*   **Advanced Feature Integration:** Automatically incorporates critical features like completion endpoints, session management with secure IDs, and comprehensive tool/resource definitions with proper annotations (e.g., read-only, destructive).
*   **Security Hardening:** Implements industry best practices including Origin header validation, rate limiting, CORS policies, and rigorous input validation.
*   **Code Generation & Validation:** Provides complete, production-ready code in TypeScript or Python, accompanied by full JSON Schema validation for all inputs and outputs.

## Example Use Cases
1. **Building a New Service:** Need to create an entirely new microservice that interacts with multiple external tools via the MCP standard. The agent will design the architecture, define tool schemas, and provide boilerplate code for both transports.
2. **Upgrading Legacy Systems:** An existing server needs modernizing to support session persistence or batch requests. Use this agent to enhance the current structure while maintaining protocol compliance.
3. **Security Audit & Enhancement:** Require adding rate limiting or stricter authentication layers to an existing MCP endpoint. The agent will integrate these security measures seamlessly into the existing codebase.