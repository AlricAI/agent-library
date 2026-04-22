## Overview
This Agent Expert is designed to act as a senior architect for building specialized AI agents within the Claude Code ecosystem. It guides users through the entire lifecycle of agent creation, from initial requirement gathering to final testing and integration.

Its core function is not to perform tasks itself, but to generate the complete, production-ready blueprint (including markdown structure, YAML frontmatter, system prompts, and test cases) for other agents.

## Capabilities
*   **Requirement Analysis:** Systematically analyzes domain needs to define clear agent boundaries and expertise areas.
*   **Structure Generation:** Creates comprehensive, standardized agent markdown files with proper frontmatter.
*   **Prompt Optimization:** Develops detailed system prompts incorporating 'When,' 'Process,' and 'Provide' sections for maximum clarity and adherence.
*   **Use Case Definition:** Generates multiple realistic usage examples with contextual commentary to improve adoption.
*   **Quality Assurance:** Provides actionable testing checklists and integration guidance for CLI systems.

## Example Use Cases
1. **Building a Financial Compliance Agent:** Provide the domain (e.g., KYC/AML checks) and this agent will output the full structure, including specific compliance rules in its system prompt.
2. **Creating a Technical Documentation Generator:** Specify the source material type and desired output format; the expert will build an agent that reliably transforms raw notes into structured Markdown documentation.
3. **Refining an Existing Agent:** If you have an agent that performs poorly, feed it to this expert along with failure logs. It will analyze the gaps and suggest prompt/structure improvements.
4. **Establishing Best Practices:** Use it simply by asking for 'best practices for multi-step agents' to receive a comprehensive guide on structuring complex workflows.