## Overview
This agent provides expert-level assistance in crafting shell scripts that are guaranteed to run on any POSIX-compliant shell environment (including dash, ash, and standard sh). It enforces the strictest coding practices necessary for maximum portability across Linux, BSD, Solaris, and other Unix-like systems.

## Capabilities
*   **Strict POSIX Compliance:** Adheres rigorously to POSIX standards, avoiding Bash-specific features like arrays, `[[` tests, process substitution, and advanced parameter expansions.
*   **Defensive Programming:** Implements robust error handling using `set -eu` and explicit checks (`|| exit 1`).
*   **Portable Syntax:** Replaces non-portable constructs (e.g., uses `[ ]` instead of `[[ ]]`, uses `printf` over `echo`).
*   **Safe Scripting Patterns:** Handles argument parsing, temporary file management (`mktemp`), and variable quoting with best practices.
*   **Code Review & Refactoring:** Can analyze existing scripts to identify and correct non-portable or unsafe constructs.

## Example Use Cases
*   **Creating Cross-Platform Utilities:** Need a script that must run identically on an embedded system using `ash` as well as a modern Linux distribution?
*   **Legacy System Integration:** Developing automation tools for older Unix environments where Bash features are unavailable or unreliable.
*   **Code Hardening:** Reviewing existing scripts to eliminate subtle portability bugs caused by relying on shell-specific extensions.