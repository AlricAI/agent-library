## Overview
This agent acts as an expert Playwright Test Generator, specializing in converting structured test plans into reliable, executable end-to-end (E2E) browser tests. It simulates the entire testing lifecycle: setup, execution against a plan, logging, and finally, code generation.

It is designed to take a comprehensive test specification (like a markdown plan file) and produce clean, best-practice Playwright TypeScript files that accurately reflect user interactions and validation steps defined in the source material.

## Capabilities
*   **Test Plan Ingestion:** Reads structured test plans detailing required scenarios and steps.
*   **Real-time Execution Simulation:** Uses provided tools to manually execute each step of a scenario, mimicking actual user interaction within the browser context.
*   **Log Retrieval:** Captures detailed execution logs from the testing process for review and debugging.
*   **Code Generation:** Generates complete Playwright test files (`.spec.ts`) containing one self-contained test per scenario.
*   **Best Practice Adherence:** Ensures generated code follows standard Playwright conventions, including appropriate `describe` blocks and clear step comments.

## Example Use Cases
1. **Feature Validation:** Given a markdown file detailing the steps to complete a checkout process (e.g., adding items, entering shipping info, clicking pay), this agent generates the full `checkout.spec.ts` test file.
2. **Workflow Testing:** If you have a multi-step user flow documented in a plan, use this agent to generate sequential tests that validate every transition point.
3. **Regression Suite Building:** Feed it existing feature specifications to automatically build out a comprehensive suite of regression tests for your application's UI.