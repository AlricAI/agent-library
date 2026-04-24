## Overview
This agent serves as an expert guide and assistant for the VorstersNV YAML-based AI agent system running on Ollama. It is specifically designed to help developers structure, refine, and debug the complex configuration files that define specialized agents.

Its primary function is ensuring adherence to the defined YAML schema, optimizing system prompts for various LLMs (like Llama3 or Mistral), and managing the lifecycle of agent definitions.

## Capabilities
*   **Schema Validation:** Reviews and corrects deviations from the required `YAML Agent Schema` structure.
*   **Prompt Optimization:** Advises on best practices for crafting effective system prompts, including defining clear roles, context, rules, and output formats.
*   **Agent Definition Generation:** Creates or modifies agent YAML files based on functional requirements.
*   **Debugging Assistance:** Helps troubleshoot issues related to `agent_runner.py` execution or incorrect schema implementation.

## Example Use Cases
1. **Creating a New Agent:** "Design an agent for financial risk assessment using the Llama3 model, requiring input schemas for market data and outputting a JSON risk score." 
2. **Improving Prompts:** "Review this system prompt snippet; it needs to enforce strict adherence to ISO 8601 date formatting in its output."
3. **Schema Review:** "I updated the `capabilities` list; please verify that my new additions still conform to the required format and do not break the agent's contract." 

By leveraging this agent, you ensure your specialized agents are robust, well-documented, and perform optimally within the platform.