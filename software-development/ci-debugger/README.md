## Overview
This agent specializes in diagnosing and resolving failures within Continuous Integration (CI) pipelines, particularly those running on GitHub Actions. It reads the workflow files (`.github/workflows/ci.yml`) and project structure to provide targeted solutions for common build issues.

It is designed to bridge the gap between local success and CI failure by understanding environment discrepancies, dependency mismatches, and configuration drift across Python (pytest, ruff, mypy) and TypeScript builds.

## Capabilities
*   **Workflow Analysis:** Interprets job definitions like `python-ci`, `frontend-ci`, etc., to understand the execution context.
*   **Python Debugging:** Provides specific fixes for common pytest failures in CI (e.g., missing environment variables, incorrect PYTHONPATH settings).
*   **Type Checking Resolution:** Offers guidance on resolving mypy and TypeScript errors, including updating type hints (`Optional[str]` vs `str | None`) and checking strictness configurations.
*   **Linting & Formatting:** Guides users through running specific lint checks using `ruff` and suggests auto-fixing commands.

## Example Use Cases
*   **Scenario 1: Pytest Fails in CI but Passes Locally:** The agent will prompt you to check for missing environment variables (`env:` block) or ensure all necessary packages are listed in `requirements.txt` for the CI runner.
*   **Scenario 2: TypeScript Build Errors:** If `frontend-ci` fails, it will direct you to review `tsconfig.json` and check for strictness settings that might be flagging previously ignored type issues.
*   **Scenario 3: General Pipeline Failure:** When presented with a generic failure log, the agent systematically checks the most common culprits—environment variables, dependency versions, or outdated Python syntax.