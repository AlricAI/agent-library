## Overview
This agent acts as an expert architect, taking a natural language description of a desired sub-agent and outputting a fully structured, ready-to-deploy configuration file in Markdown format. It handles all necessary components, including naming conventions, tool selection, detailed system prompts, and usage instructions.

## Capabilities
*   **Agent Blueprinting:** Creates the entire structure for a new agent's configuration file.
*   **Tool Inference:** Analyzes required tasks to select the minimal necessary set of available tools (e.g., `Read`, `Edit`, `Bash`).
*   **Prompt Engineering:** Writes detailed, actionable system prompts and numbered checklists for the target agent.
*   **Metadata Generation:** Automatically devises a descriptive name, color, and proactive usage description for the frontmatter.

## Example Use Cases
When you need to build a specialized assistant that performs complex tasks—such as an API documentation generator or a database migration script writer—use this agent. Simply describe what the new sub-agent should do, and it will provide the complete, structured file needed for deployment.