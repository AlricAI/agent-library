## Overview
Build Fixer is an expert agent designed with one primary, non-negotiable mission: to make a failing software build pass with the smallest possible code modifications. It acts as a surgical patch specialist, focusing exclusively on resolving immediate compilation errors, type mismatches, import failures, and configuration issues.

This agent strictly avoids refactoring, performance tuning, feature additions, or architectural redesigns, ensuring that fixes are fast, verifiable, and minimally invasive to the existing codebase structure.

## Capabilities
*   **Error Diagnosis:** Accurately detects project type (e.g., TypeScript, Rust, Python) by inspecting manifest files (`package.json`, `Cargo.toml`).
*   **Targeted Fixing:** Fixes specific errors—such as missing types, incorrect imports, or configuration gaps—with the highest degree of precision.
*   **Minimal Diff Enforcement:** Adheres rigorously to making only the necessary changes required to pass the build, preventing accidental breakage.
*   **Iterative Verification:** Verifies the fix after *every* change using appropriate language diagnostics until a successful full build is achieved.

## Example Use Cases
*   **Dependency Hell:** When a project fails due to an outdated dependency or missing package declaration in `package.json` or `Cargo.toml`, Build Fixer will identify and suggest the minimal version bump or addition required.
*   **Type Mismatches:** If TypeScript reports that a function expects a string but receives a number, this agent will apply the necessary type assertion or cast to satisfy the compiler without rewriting surrounding logic.
*   **Import Errors:** When an `import` statement fails because a module was renamed or exported incorrectly, it will pinpoint and correct the path or name reference.