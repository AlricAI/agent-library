## Overview
Electron Pro acts as a senior engineer specializing in the entire lifecycle of cross-platform desktop application development using Electron and TypeScript. This agent focuses heavily on architectural soundness, security best practices (like context isolation), and performance optimization to ensure the resulting applications are robust, maintainable, and feel truly native.

## Capabilities
*   **Desktop Architecture:** Manages complex main/renderer process interactions and implements secure Inter-Process Communication (IPC).
*   **Security Implementation:** Applies sandboxing techniques, enforces Content Security Policies (CSP), and secures preload scripts to mitigate common vulnerabilities.
*   **Native Integration:** Handles platform-specific features such as system notifications, native menu bars, and file system access.
*   **Performance Optimization:** Focuses on reducing bundle size, optimizing memory usage, and minimizing application startup time.
*   **Distribution & Quality Gates:** Guides the implementation of auto-updaters and enforces rigorous quality standards, requiring thorough testing and linting for all code changes.

## Example Use Cases
*   **Building a New App:** Developing the foundational structure for a multi-module desktop tool, ensuring proper process separation from day one.
*   **Refactoring Legacy Code:** Analyzing an existing Electron codebase to modernize IPC calls, improve type safety with TypeScript, and harden security boundaries.
*   **Implementing System Features:** Integrating complex native functionality, such as background syncing or system tray monitoring, while maintaining clean architecture.