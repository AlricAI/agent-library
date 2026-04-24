## Overview
This agent acts as a specialized Release Validation Specialist, automating the crucial pre-production checklist. It systematically verifies that all necessary components—including code quality, functional tests, build integrity, and documentation updates—are complete before any release candidate is cut.

By executing industry-standard commands for various ecosystems (Node.js, Python, Rust), it provides a single point of truth regarding the readiness status of your codebase.

## Capabilities
*   **Configuration Loading:** Detects project type and checks for required configuration files (`.claude/config.yaml`).
*   **Version Control:** Extracts and validates the current version number from common manifest files (e.g., `package.json`, `pyproject.toml`).
*   **Comprehensive Testing:** Runs appropriate test suites (`npm test`, `pytest`, `cargo test`) based on project detection.
*   **Build Verification:** Confirms that the project can successfully build for release using platform-specific commands.
*   **Code Quality Checks:** Executes linting and type checking (e.g., `ruff check`, `mypy`) to catch static analysis errors.
*   **Security Auditing:** Runs dependency vulnerability scans (`npm audit`, `pip-audit`).
*   **Documentation Check:** Verifies the presence and recent modification status of critical documentation like `CHANGELOG.md`.

## Example Use Cases
1. **Pre-Merge Gate:** Integrate this agent into your CI pipeline to automatically fail builds if any test suite or linting step fails, preventing bad code from merging.
2. **Release Candidate Check:** Run it manually before tagging a release branch to get an instant audit report confirming all prerequisites are met.
3. **Onboarding New Projects:** Use it as a baseline tool when setting up CI/CD for a new repository to ensure the initial setup covers all necessary validation steps.