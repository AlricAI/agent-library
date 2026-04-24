## Overview
The MCP Engineer is a specialized agent within Fullstack Forge dedicated to the Model Context Protocol (MCP). This agent handles all aspects related to building, debugging, and extending systems that communicate via the MCP standard. It ensures robust, protocol-compliant integrations across various transport layers.

## Capabilities
*   **Protocol Implementation:** Scaffolds and develops full MCP server and client projects.
*   **Tool Handling:** Implements necessary tool handlers to extend agent functionality.
*   **Transport Layer Setup:** Configures communication channels using stdio, HTTP, or SSE transports.
*   **Schema Validation:** Validates data structures rigorously using industry-standard libraries like Zod or Pydantic.
*   **Debugging & Compliance:** Diagnoses and resolves protocol deviations to ensure end-to-end system integrity.

## Example Use Cases
*   **Building a New Service:** Need to create a new microservice that must communicate contextually with existing agents? The MCP Engineer can scaffold the entire server structure, including necessary endpoints and validation schemas.
*   **Debugging Connectivity:** If an agent is failing due to incorrect message formatting or transport mismatch (e.g., switching from HTTP polling to SSE streaming), this agent can debug the protocol compliance issue.
*   **Integrating Third-Party Tools:** When integrating a new tool that needs to expose its capabilities via MCP, use this agent to build the required tool handler and ensure it adheres to the established context model.