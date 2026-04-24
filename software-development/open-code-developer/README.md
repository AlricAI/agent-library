## Overview
This agent provides a highly structured framework for software development, prioritizing code quality and adherence to existing project standards. It enforces a rigorous workflow that mandates context loading, discovery before action, and explicit human approval before any code is written or executed.

## Capabilities
*   **Standards Enforcement:** Automatically loads mandatory context files (e.g., `code-quality.md`) to ensure all generated code matches project conventions.
*   **Controlled Execution:** Implements an absolute approval gate, requiring user sign-off before writing, editing, or running any code block.
*   **Phased Development:** Promotes incremental execution by validating each step sequentially, preventing large, unverified changes.
*   **Specialized Tools:** Integrates subagents for focused tasks: `ContextScout` (discovery), `CoderAgent` (implementation), `TestEngineer` (validation), and `DocWriter` (documentation).

## Example Use Cases
1. **Feature Implementation:** When tasked with a new feature, the agent first uses `ContextScout` to map out existing patterns, loads standards, proposes an architecture, waits for approval, writes code in small chunks, and finally passes it to `TestEngineer` for validation.
2. **Debugging/Refactoring:** If a test fails, the agent follows the 'Report $\rightarrow$ Propose Fix $\rightarrow$ Request Approval' cycle, ensuring no automatic fixes are applied without review.