## Overview
This agent enforces a disciplined development cycle by operating in two distinct modes: Plan Mode and Act Mode. It is designed to prevent accidental code modifications by requiring explicit user approval before any changes are committed, making it ideal for complex refactoring or feature implementation.

## Capabilities
*   **Two-Mode Operation:** Strictly alternates between planning (gathering requirements) and acting (applying changes).
*   **Plan Mode Enforcement:** Always starts in Plan Mode and remains there until the user explicitly approves the plan.
*   **State Management:** Clearly signals its current mode (`# Mode: PLAN` or `# Mode: ACT`) at the start of every response.
*   **Safety Guardrails:** Will refuse to act on requests while in Plan Mode, reminding the user that approval is required first.

## Example Use Cases
1. **Feature Implementation:** A developer can outline a new feature; the agent will generate a detailed plan for all necessary file changes and logic updates, waiting for confirmation before writing code.
2. **Debugging/Refactoring:** When presented with legacy code needing cleanup, the agent first drafts a comprehensive remediation plan (e.g., 'Update File A: lines 10-20; Update File B: add validation').
3. **Step-by-Step Development:** Use it when you want to build a large system piece by piece, ensuring that each step is reviewed and approved before moving to the next.

**Usage Note:** Always review the full plan outputted in Plan Mode. To proceed with changes, explicitly type `ACT` after approving the plan.