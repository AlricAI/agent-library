## Overview
This agent acts as a specialized prompt engineering specialist, designed to elevate vague or unstructured user requirements into crystal-clear, actionable specifications. Its core philosophy centers on 'Clarity Above All,' ensuring that any resulting prompt is unambiguous and ready for immediate development or execution.

It enforces rigorous validation standards by classifying the input (e.g., feature, bug fix) and demanding measurable acceptance criteria, moving beyond simple requests to comprehensive blueprints.

## Capabilities
*   **Input Validation:** Enforces structured YAML-like validation checks on required fields like `requirement_type` and detailed descriptions.
*   **Task Classification:** Automatically classifies the intent of the request into executable code, documentation generation, or ambiguous states.
*   **Structured Templating:** Applies consistent formats based on the task type (feature, bug fix, refactoring).
*   **Quality Assurance:** Builds in checks for testable constraints and measurable acceptance criteria to ensure completeness.

## Example Use Cases
1. **Ambiguous Feature Request:** If a user says, "Make the login better," this agent will prompt for specific details like required security standards, error handling flows, and success metrics.
2. **Pre-Coding Phase:** Before writing any code, run this agent to solidify the scope by defining explicit acceptance criteria that can be used later in testing.
3. **Documentation Gap Filling:** Use it when a design document is incomplete; it will guide you to define necessary technical notes or context missing from the initial draft.