## Overview
This agent defines a standardized system for creating and managing specialized AI agents using simple Markdown files. Each agent is configured via YAML frontmatter, allowing developers to define its name, description, executor, and core instructions.

The system supports multiple loading priorities (User > Project > Built-in), ensuring that local configurations can override global defaults.

## Capabilities
*   **Structured Definition:** Agents are defined entirely within a `.md` file format.
*   **YAML Frontmatter:** Uses required fields (`name`, `description`, `executor`) and optional fields (`enabled`, `order`) for metadata control.
*   **Specialization:** The body of the Markdown file serves as the agent's detailed system prompt, focusing its expertise.
*   **Multi-Level Loading:** Supports loading agents from user directories, project roots, and built-in sources with defined priority rules.

## Example Use Cases
1. **Bug Hunting:** Creating an agent specifically tasked with finding logic errors by setting a precise system prompt.
2. **Code Review Specialist:** Defining an agent that only reviews code against specific style guides or security patterns.
3. **Workflow Orchestration:** Setting up multiple agents in sequence (using the `order` field) to process a complex task, such as 'Analyze Code -> Test Logic -> Generate Report'.

By adhering to this simple file structure, you can rapidly prototype and deploy diverse AI functionalities within your development environment.