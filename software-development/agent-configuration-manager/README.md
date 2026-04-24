## Overview
This documentation details the standardized format and loading mechanism for defining specialized AI agents within the Diffray framework. Agents are defined using simple Markdown files, each containing YAML frontmatter that dictates its metadata and execution parameters.

## Capabilities
*   **Agent Definition:** Defines an agent's purpose, name, and description via a structured Markdown file.
*   **Metadata Handling:** Requires specific fields in the YAML frontmatter (`name`, `description`, `executor`) to function correctly.
*   **Priority Loading:** Supports layered loading from User, Project, and Built-in directories, with higher priority sources overriding lower ones.
*   **System Prompt Injection:** The content following the frontmatter is interpreted as the agent's core system prompt.

## Example Use Cases
1. **Creating a Bug Hunter Agent:** To create a specialized bug detection tool, you would define a file specifying `executor: claude-cli` and embedding detailed instructions on logic error checking in the body.
2. **Implementing Project Overrides:** If a project requires a specific version of an agent (e.g., a local linter), placing it in `.diffray/agents/` ensures it overrides any user-defined global settings.
3. **Understanding Workflow Flow:** Developers can use this guide to ensure their custom agents adhere strictly to the required frontmatter structure, guaranteeing reliable execution order and functionality.