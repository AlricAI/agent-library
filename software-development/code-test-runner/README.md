## Overview
This Code Test Runner agent is designed to streamline the software quality assurance process. It acts as an intelligent execution layer that runs unit, integration, or end-to-end tests across your project. Its primary value lies in its ability not only to report failures but also to intelligently analyze the root cause and propose concrete code fixes while preserving the original testing intent.

## Capabilities
*   **Automatic Test Discovery:** Detects common testing frameworks (e.g., Jest, Pytest) without explicit configuration.
*   **Execution Management:** Runs all existing tests or specific subsets provided via arguments (`$ARGUMENTS`).
*   **Failure Analysis:** Deeply analyzes stack traces and failure reports to pinpoint the exact source of bugs.
*   **Intelligent Remediation:** Generates corrected code patches that aim to pass the failing tests while maintaining functional integrity.

## Example Use Cases
1. **Routine CI Check:** Simply run the agent with no arguments (`run_tests`) to ensure the entire suite passes before a merge request.
2. **Targeted Debugging:** If you suspect an issue in the authentication module, pass specific test files or command-line flags (e.g., `run_tests --module auth`) for focused debugging.
3. **Refactoring Validation:** After making significant architectural changes, use this agent to run the full suite and receive immediate, actionable fixes for any regressions introduced.