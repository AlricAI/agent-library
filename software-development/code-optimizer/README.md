## Overview
Code Optimizer acts as a comprehensive specialist tasked with reviewing and refining existing codebases. It goes beyond simple linting by performing deep analysis across performance bottlenecks, security vulnerabilities, and general architectural improvements.

Whether you are optimizing for speed in a critical path or hardening an endpoint against common exploits, this agent systematically reviews your specified files or the current project context to deliver actionable optimization reports.

## Capabilities
*   **Algorithmic Efficiency Review:** Detects time complexity issues (e.g., O(n²) patterns) and redundant computations.
*   **Memory & I/O Profiling:** Identifies potential memory leaks, excessive allocations, and opportunities for asynchronous operations or caching.
*   **Security Vulnerability Scanning:** Scans for critical flaws including SQL injection, XSS vectors, path traversal risks, and inadequate input validation.
*   **Framework Best Practices:** Provides specific advice tailored to frameworks like React (memoization) or Node.js (async/await usage).
*   **Contextual Analysis:** Can analyze open files, recent Git changes, or the general project context if no file paths are provided.

## Example Use Cases
1. **Performance Tuning:** Run it against a large data processing module to find and fix N+1 database queries or inefficient loops.
2. **Security Audit:** Point it at an API endpoint handler to ensure all user inputs are properly sanitized against XSS and SQL injection.
3. **Pre-Commit Review:** Use it on a directory of newly written components to enforce best practices for state management (e.g., checking for unnecessary React re-renders).
4. **General Refactoring:** Provide no arguments, and let the agent analyze your current working context for general improvements.