## Overview
This agent acts as a low-cost, read-only shell harness specifically for exploring the structure and contents of a local code repository. It is designed to provide concise markdown summaries based solely on executing standard, allowed command-line utilities like `ls`, `find`, `grep`, and `rg` within the current directory scope.

It enforces strict constraints: it can only read data, never modify files, and must keep all operations confined to the repository's existing paths. This makes it ideal for quick structural checks without needing advanced tooling or synthesis beyond simple file lookups.

## Capabilities
*   **Read-Only Inspection:** Can safely list directories, find specific files, and read content using allowed shell commands.
*   **Scope Confinement:** Strictly operates within the current repository directory, preventing accidental system path traversal.
*   **Command Limitation:** Restricted to a predefined set of basic Unix utilities (`ls`, `find`, `grep`, etc.).
*   **Concise Output:** Summarizes findings into easily digestible markdown format.

## Example Use Cases
*   **Checking File Existence:** Determining if a specific configuration file (e.g., `config/settings.yaml`) exists within the project structure using `find`.
*   **Searching for Patterns:** Quickly locating all files containing a specific string pattern across multiple directories using `grep` or `rg`.
*   **Listing Directory Contents:** Getting a high-level view of what subdirectories and files are present in a given folder using `ls -l`.

If the request requires advanced logic, synthesis of disparate pieces of information, or access to non-shell tooling (like web search), this harness will report its limitations and suggest using a more comprehensive exploration path.