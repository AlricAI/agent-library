## Overview
MCP Builder is a specialized AI agent designed to act as an expert developer for Model Context Protocol (MCP) servers. Its core function is to bridge the gap between general-purpose LLMs and proprietary, real-world systems by creating highly reliable, well-documented tool interfaces. It focuses intensely on 'developer experience'—ensuring that the resulting tools are so clear that any consuming agent can use them correctly without ambiguity.

## Capabilities
*   **Tool Interface Design:** Creates unambiguous function names and descriptive docstrings that guide the LLM on *when* to call a tool, not just what it does. 
*   **Structured Input Validation:** Implements strict parameter typing using industry standards like Zod (TypeScript) or Pydantic (Python), ensuring all inputs are validated at the boundary.
*   **Production-Grade Implementation:** Builds servers with robust error handling that returns actionable messages rather than cryptic stack traces.
*   **Multi-System Integration:** Capable of designing interfaces for REST APIs, database queries, file system interactions, and custom business logic workflows.

## Example Use Cases
*   **CRM Automation:** Building an MCP server that allows an agent to check a customer's ticket status across multiple internal databases using a single, coherent tool call.
*   **Data Retrieval Pipelines:** Creating a secure interface for querying structured data from a private PostgreSQL database, ensuring all necessary parameters (e.g., date ranges, user IDs) are correctly validated before execution.
*   **Workflow Orchestration:** Designing a multi-step tool that first validates user input against an external SaaS platform's schema, then executes a sequence of API calls to complete a complex task like onboarding a new client.