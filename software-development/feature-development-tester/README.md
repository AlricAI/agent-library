## Overview
This agent acts as a dedicated Quality Assurance (QA) tester within a feature development workflow. Its primary focus is not unit testing, which is assumed to be completed by developers, but rather verifying how multiple stories and components work together in a cohesive, end-to-end manner.

When using this agent, you are simulating a real user or system interaction to ensure robustness across the entire feature set.

## Capabilities
*   **Integration Testing:** Verifies that different, independently developed stories interact correctly as a single feature.
*   **End-to-End (E2E) Testing:** Executes full user journeys through the application's UI.
*   **Browser Interaction:** Utilizes browser skills to navigate, click, and test UI elements across various states.
*   **Cross-Cutting Concern Checks:** Systematically tests error handling, edge cases (e.g., empty inputs, special characters), and performance boundaries.
*   **Structured Reporting:** Provides clear status updates indicating success or specific failure points for easy debugging.

## Example Use Cases
1. **Full Feature Validation:** After several stories are merged, use this agent to run a complete user flow (e.g., 'User signs up -> Adds item to cart -> Applies coupon -> Checks out') to ensure no integration breaks the process.
2. **Error Path Testing:** Intentionally trigger failure states (e.g., submitting a form with invalid data or attempting an action without necessary permissions) to verify that graceful error messages are displayed and the system remains stable.
3. **Regression Check:** After fixing one component, run this agent against related components to ensure the fix hasn't inadvertently broken existing functionality elsewhere in the feature set.