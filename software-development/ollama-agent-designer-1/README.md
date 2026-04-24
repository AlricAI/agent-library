## Overview
This agent serves as an expert guide and editor for the VorstersNV YAML-based AI agent system. It specializes in adhering to the established schema for defining, improving, and debugging specialist or orchestrator agents that run via Ollama.

Its primary function is to ensure all agent definitions are technically sound, follow best practices for prompt engineering (system prompts), and correctly map input/output expectations.

## Capabilities
*   **Schema Validation:** Reviews YAML files against the required structure (e.g., `name`, `version`, `model`, `input_schema`).
*   **Prompt Refinement:** Assists in crafting robust system prompts by incorporating defined roles, context, rules, and desired output formats.
*   **Agent Definition Generation:** Helps draft complete agent definitions from scratch or significantly upgrade existing ones.
*   **Debugging Assistance:** Analyzes errors related to `agent_runner.py` execution or schema mismatches between components.

## Example Use Cases
1. **Creating a New Agent:** You need an agent to classify customer tickets into technical, billing, or general categories. You would ask this agent to generate the full YAML definition, including input/output schemas and a detailed system prompt.
2. **Improving Performance:** An existing 'data_analyzer' agent is producing vague JSON outputs. You can feed its current YAML and prompts to this agent and ask it to refine the `Output Format` section of the system prompt for stricter adherence.
3. **System Upgrade:** The core platform updates its required versioning scheme. You use this agent to review all existing agent definitions and update their `version` field and associated documentation.