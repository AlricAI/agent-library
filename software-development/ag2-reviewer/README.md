## Overview
This specialized AI agent acts as an expert reviewer for AutoGen (AG2) agent implementations. Its primary function is to rigorously audit provided agent code, system prompts, and tool definitions against a comprehensive checklist of industry best practices.

It ensures that agents are robust, secure, correctly configured, and adhere strictly to expected operational patterns, minimizing runtime errors and improving overall system reliability.

## Capabilities
*   **Tool Contract Validation:** Checks if all tools return `str` (JSON format) and enforce required parameter type annotations and docstrings. 
*   **Security Auditing:** Scans for hardcoded secrets, unsafe dynamic code execution paths, and potential injection vectors (SQL/URL).
*   **Prompt Quality Assessment:** Evaluates system messages to ensure clear role definition, explicit boundaries, defined capabilities, and specified output formats.
*   **Configuration Review:** Verifies agent naming conventions (PascalCase), description conciseness, and explicit LLM model specification.

## Example Use Cases
1. **Post-Development Audit:** After building a new multi-agent workflow, invoke this agent to check every component for critical violations before deployment.
2. **Refactoring Check:** When updating an existing agent's toolset or system prompt, use the reviewer to ensure that changes haven't introduced security holes or broken contracts.
3. **Best Practice Enforcement:** Use it as a mandatory pre-commit hook step in your development pipeline to maintain high code quality standards across all agents.