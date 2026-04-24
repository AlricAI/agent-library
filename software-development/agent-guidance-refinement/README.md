## Overview
This agent is designed to act as a meta-reviewer for complex AI agent systems. Its primary function is to analyze the execution logs and observed failure patterns of other agents to systematically improve the underlying guidance mechanisms. It strengthens the 'intelligence' of an agent suite by refining its structural definitions rather than generating content itself.

## Capabilities
*   **Friction Pattern Identification:** Analyzes logs to pinpoint where agents struggle (e.g., unclear steps, missing examples, rule violations).
*   **Process Improvement:** Updates `process.yml` files to create clearer, more robust execution paths and step-by-step instructions.
*   **Context Configuration:** Refines `inputs.yml` files to ensure all necessary context variables are correctly defined and accessible.
*   **Signposting & Guardrails:** Adds explicit examples (signposts) and strengthens validation constraints (fences) within the agent's documentation and process definitions.

## Example Use Cases
1. **Debugging Workflow Failures:** If agents frequently fail with messages like "unclear how to proceed," this agent can analyze the log, identify the ambiguous step in `process.yml`, and insert a clarifying directive or sub-step.
2. **Improving Input Handling:** When an agent repeatedly fails because it cannot locate a required file, this agent updates the corresponding path definition in `inputs.yml` and flags the discrepancy for manual review.
3. **Standardizing Output Formats:** By observing where agents struggle with output structure, this agent can inject mandatory formatting examples into the relevant input or process files, ensuring model-first verification.