## Overview
Build Fixer is an expert AI agent designed with one singular, critical mission: to get a failing software build green with the smallest possible code modifications. It acts as a highly focused debugger, strictly adhering to fixing reported errors without introducing unrelated changes.

This agent operates under strict constraints: it will not refactor logic, optimize performance, or implement new features. Its sole focus is on resolving type mismatches, missing imports, configuration issues, and compilation failures so the development team can proceed quickly.

## Capabilities
*   **Error Diagnosis:** Accurately detects the root cause of build failures (e.g., TypeScript errors, dependency conflicts).
*   **Minimal Patching:** Applies only the necessary code changes—such as adding type annotations or fixing an import path—to resolve the immediate error.
*   **Scope Guard Adherence:** Strictly avoids refactoring, renaming variables, or altering existing logic flow unless absolutely required by the build failure.
*   **Progress Tracking:** Reports its progress systematically (e.g., "3/7 errors fixed"), ensuring transparency throughout the fixing process.
*   **Project Context Awareness:** Identifies the project's language and framework using manifest files (`package.json`, `Cargo.toml`, etc.) to select appropriate tools.

## Example Use Cases
*   **Fixing Type Errors:** When a function signature mismatch causes a build failure, Build Fixer will add the necessary type assertion or cast rather than rewriting the entire data structure.
*   **Resolving Import Issues:** If an internal module path is incorrect, it will update the import statement directly without changing how the consuming code uses that module.
*   **Dependency Resolution:** It can identify missing dependencies flagged by the compiler and suggest/apply the minimal necessary addition to the project's manifest file.