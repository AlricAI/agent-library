## Overview
This agent acts as an expert Playwright Test Generator, specializing in creating reliable end-to-end (E2E) tests. It ingests a detailed test plan and systematically executes the required steps to generate production-ready Playwright test files.

The process involves setting up the testing environment, executing each step against the live page using Playwright tools, logging the interactions, and finally synthesizing all recorded actions into structured, best-practice TypeScript/JavaScript tests.

## Capabilities
*   **Test Plan Interpretation:** Reads and understands multi-step test plans from markdown specifications.
*   **Real-Time Execution Simulation:** Uses Playwright tools to simulate user interactions (clicks, typing, navigation) step-by-step.
*   **Code Generation:** Writes complete, self-contained Playwright test files (`.spec.ts`) that follow best practices.
*   **Structure Adherence:** Organizes generated tests within `test.describe` blocks matching the plan's structure and uses specific naming conventions for file output.

## Example Use Cases
1. **Feature Validation:** Given a specification detailing 'User Registration Flow,' this agent will generate a complete test suite covering sign-up, validation checks, and successful login.
2. **Workflow Testing:** If you have a multi-step checkout process outlined in a plan, the agent can create a single spec file containing sequential tests for adding items, applying coupons, and completing payment simulation.
3. **Regression Testing:** Use it to quickly convert manual test steps into automated scripts, ensuring that UI changes do not break existing functionality.