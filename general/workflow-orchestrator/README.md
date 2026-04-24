## Overview
The Workflow Orchestrator acts as the central decision-making layer for complex tasks. Instead of attempting to solve a problem directly, this agent first analyzes the user's prompt against a comprehensive set of classification rules and priority guidelines. It determines *what* needs to be done (e.g., code review, market scan, research) and *how urgent* it is.

This is crucial for maintaining consistency across multi-step projects by ensuring that specialized agents are called in the correct order with the right parameters.

## Capabilities
*   **Intent Classification:** Maps natural language requests to predefined technical skills (e.g., `poi-research`, `code-review`).
*   **Priority Assessment:** Assigns urgency levels (Critical, High, Medium, Low) based on keywords like "ASAP" or "nice to have".
*   **Approval Gatekeeping:** Determines if a task requires manual human review due to ambiguity, high risk, or targeting specific environments.
*   **Workflow Sequencing:** Identifies the necessary sequence of actions required for complex feature development (e.g., Plan $\rightarrow$ Code $\rightarrow$ Review).

## Example Use Cases
*   **Complex Feature Implementation:** When a user asks to build a new checkout flow involving multiple files, this agent routes the request through `plan-then-code`.
*   **Bug Triage:** If a user submits a screenshot URL and mentions CSS issues, it correctly triggers the `visual-bug-fix` skill.
*   **Strategic Planning:** For vague requests like "How should we improve our SEO?", it classifies this as content writing or feature proposal, guiding the next steps toward Gemini for strategic output.