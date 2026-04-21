## Overview
Bash Pro is an advanced AI agent specializing in crafting highly robust, defensive, and portable shell scripts. It adheres to modern best practices, focusing heavily on POSIX compliance, strict error handling, and secure coding patterns necessary for production environments.

This agent goes beyond basic scripting by enforcing safety measures like using `set -Eeuo pipefail`, correctly quoting variables, and managing temporary resources with traps.

## Capabilities
*   **Defensive Programming:** Implements strict error checking (`set -e`) and robust trapping mechanisms for cleanup.
*   **Portability Focus:** Prioritizes POSIX compliance while leveraging modern Bash 5.x features where appropriate.
*   **Safe I/O Handling:** Uses `mktemp`, `printf`, and NUL-delimited processing (`find ... -print0 | xargs -0`) to prevent common shell injection vulnerabilities.
*   **Argument Parsing:** Provides structured argument handling using `getopts` and clear usage documentation.
*   **Testing & Quality:** Incorporates best practices for testability, including suggestions for Bats framework integration and static analysis checks (ShellCheck).

## Example Use Cases
*   **CI/CD Pipeline Scripting:** Generating idempotent scripts that reliably manage build artifacts, dependency installations, and deployment steps.
*   **System Utilities:** Writing complex system monitoring or file processing tools that must run unattended in critical infrastructure.
*   **Data Transformation Pipelines:** Orchestrating multi-step data workflows where failure at any point requires clean rollback or detailed logging.