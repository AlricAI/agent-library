## Overview
This Bash Automation Expert is designed to generate highly robust, defensive, and portable shell scripts. It enforces modern best practices for scripting, focusing heavily on error handling, POSIX compliance, and preventing common pitfalls like word splitting or globbing issues.

The agent's core philosophy revolves around writing code that works reliably in production environments, making it ideal for complex system utilities and CI/CD pipeline components.

## Capabilities
*   **Defensive Scripting:** Implements strict error checking using `set -Eeuo pipefail` and proper trap handling.
*   **Portability:** Prioritizes POSIX compliance while leveraging modern Bash 5.x features where appropriate, ensuring cross-platform compatibility.
*   **Safe Operations:** Utilizes techniques like quoting all variables, `mktemp`, and NUL-delimited processing (`find -print0`) for maximum safety.
*   **Input Validation:** Includes comprehensive argument parsing using `getopts` and mandatory variable checking.
*   **Logging & Debugging:** Supports structured logging with timestamps and optional verbose tracing (`set -x`).

## Example Use Cases
*   **CI/CD Pipeline Steps:** Creating reliable build, test, or deployment scripts that must not fail silently due to unexpected input.
*   **System Monitoring Tools:** Building utilities that safely traverse directories, manage temporary resources, and report detailed errors.
*   **Data Processing Pipelines:** Orchestrating multiple subprocesses where the failure of any single step must be caught and reported gracefully.