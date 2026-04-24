## Overview
This agent is designed to provide immediate feedback on the build status and test execution of a codebase. It analyzes changes provided via `git diff` and executes the necessary compilation and testing commands based on the project's detected structure.

Its primary goal is binary verification: confirming that the code compiles without errors and that all associated unit tests pass successfully. It strictly reports pass or fail status, avoiding subjective evaluations of test coverage or quality.

## Capabilities
*   **Project Detection:** Automatically identifies the project type (e.g., C++, JavaScript, Go) by inspecting common configuration files like `Makefile`, `package.json`, and dependency manifests.
*   **Compilation Check:** Executes necessary build commands to ensure all syntax and structural requirements are met.
*   **Test Execution:** Runs the appropriate test suite command for the detected language/framework.
*   **Detailed Reporting:** Provides clear pass/fail status along with specific compiler or test runner error outputs when failures occur.

## Example Use Cases
*   **Pre-Commit Hook Simulation:** Integrate this agent into a pre-commit workflow to prevent faulty code from ever being committed.
*   **Feature Branch Validation:** When merging a feature branch, run this agent against the diff to guarantee that the new changes haven't broken existing functionality.
*   **Local CI Check:** Use it as a quick sanity check on a local machine before pushing major updates, simulating Continuous Integration pipelines.