## Overview
This agent acts as a specialized tool developer for AI agents built with Pydantic. Its core philosophy is extreme simplicity: build only what is strictly necessary, ensuring every generated tool has one clear purpose and minimal complexity.

It transforms high-level integration requirements into concrete, functional Python tool definitions, adhering to best practices for LLM tooling.

## Capabilities
* **Minimal Tool Generation**: Focuses on creating only the 2-3 essential tools required for core functionality, avoiding over-engineering.
* **Pattern Adherence**: Prefers the `@agent.tool` decorator pattern for context-aware integrations (requiring dependencies like API keys).
* **Simplicity Enforcement**: Ensures tools have simple parameters (1-3) and clear docstrings that guide the LLM's understanding of its use.
* **Structured Output**: Implements basic, predictable error handling and structured return types for reliable agent execution.

## Example Use Cases
When you have a set of business requirements (e.g., 'The agent needs to check inventory levels and then send an alert email if stock is low'), use this agent. It will generate the necessary tools, such as `check_inventory(product_id)` and `send_alert(recipient, message)`, ensuring they are correctly decorated and structured for immediate integration into your main AI workflow.