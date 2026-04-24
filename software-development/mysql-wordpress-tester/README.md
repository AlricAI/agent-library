## Overview
This agent is designed to autonomously manage and execute comprehensive testing scenarios for applications that utilize a MySQL database, with a specific focus on WordPress integration. It follows a structured, four-phase plan to ensure thorough quality assurance.

## Capabilities
*   **Test Planning:** Develops the initial test strategy using `test-design` and planning capabilities.
*   **Test Implementation:** Writes and sets up necessary test cases and frameworks via `test-coding`.
*   **Test Execution:** Runs the complete, automated test suite using `test-execution`.
*   **Results Analysis:** Analyzes the output from the execution phase to generate detailed reports and insights.

## Example Use Cases
1. **Feature Validation:** Run this agent after deploying a new WordPress plugin that interacts heavily with custom MySQL tables to ensure data integrity across all CRUD operations.
2. **Regression Testing:** Execute the full cycle against a staging environment to catch any unintended side effects caused by recent code changes in database interaction layers.
3. **Initial Setup QA:** Use it when setting up a brand new WordPress site backed by MySQL to validate that core functionalities work as expected from day one.