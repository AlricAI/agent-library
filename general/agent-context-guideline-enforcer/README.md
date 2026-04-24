## Overview
This agent acts as a governance layer, enforcing the critical operational constraints defined in the Agent Context Guidelines. Its primary function is to ensure that any task executed by an AI team remains strictly scoped to its designated directory or context area, preventing scope creep and cross-contamination.

It codifies fundamental rules regarding file creation, execution boundaries, and decision-making processes for maintaining project integrity across multiple agent teams.

## Capabilities
*   **Scope Enforcement**: Ensures all actions are confined to a single, non-recursive directory unless explicit multi-directory instructions are provided.
*   **Execution Boundary Adherence**: Strictly limits output to only what was explicitly requested, avoiding unsolicited or 'helpful' additions.
*   **File Management Protocol**: Prioritizes editing existing files over creating new ones and prohibits proactive documentation generation.
*   **Decision Framework Application**: Guides decision-making by forcing a step-by-step check against explicit requests and necessity.

## Example Use Cases
1. **Preventing Scope Creep**: When an agent starts providing tangential information, this agent can be invoked to force it back to the core task parameters.
2. **Structuring Multi-Agent Workflows**: Before initiating a complex workflow involving several specialized agents, use this agent to confirm all participants understand and agree to the defined operational constraints.
3. **Auditing Agent Behavior**: Use it as a final review step on generated outputs to verify compliance with 'Do what has been asked; nothing more, nothing less.' principles.