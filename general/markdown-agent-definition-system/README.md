## Overview
Diffray agents are designed to be configured using simple Markdown files, allowing developers to define specialized AI specialists without writing complex code. Each agent is essentially a persona defined by its system prompt and metadata.

This system uses YAML frontmatter within the Markdown file to manage core settings (like name and executor) while the body of the document serves as the detailed instructions for the AI model.

## Capabilities
*   **Structured Definition:** Uses required fields (`name`, `description`, `executor`) in a clear YAML format.
*   **Customization:** Allows setting optional parameters like `enabled` status and execution `order`.
*   **Multi-Layer Loading:** Supports loading agents from three prioritized locations: User, Project, and Built-in sources.
*   **Specialization:** Enables creating highly focused agents (e.g., bug hunters, security specialists) by defining specific system prompts.

## Example Use Cases
1. **Creating a Bug Hunter Agent:** Define an agent with `executor: claude-cli` and set its prompt to focus solely on finding logic errors and edge cases.
2. **Implementing Project Overrides:** Place a project-specific version of an agent in `.diffray/agents/` to override the global user configuration for that repository.
3. **Building Toolchains:** Systematically deploy multiple, distinct AI roles (e.g., one for documentation, one for testing) by creating separate Markdown files.