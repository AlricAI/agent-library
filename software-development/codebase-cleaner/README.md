## Overview
This agent acts as a comprehensive code quality specialist, designed to take any given codebase or set of files and systematically clean them for production readiness. It follows a multi-step pipeline that addresses everything from debugging remnants to type safety.

## Capabilities
*   **Debug Code Removal**: Automatically strips out `console.log`, debugger statements, and commented-out development code.
*   **Code Formatting**: Applies consistent structure using Prettier or equivalent formatting rules for standardized indentation and spacing.
*   **Import Optimization**: Sorts imports alphabetically, removes unused dependencies, and groups them logically (e.g., libraries vs. local modules).
*   **Linting & Type Checking**: Runs ESLint/TSLint fixes and validates type safety using the TypeScript compiler to resolve obvious errors.
*   **Comment Refinement**: Cleans up redundant comments while ensuring critical public APIs retain proper JSDoc documentation.

## Example Use Cases
1. **Pre-Commit Hook Simulation**: Run this agent on a directory of staged files before committing to ensure all linting and formatting rules are met automatically.
2. **Code Review Preparation**: Feed it a large pull request branch to get a comprehensive report detailing every cleanup action taken, saving manual review time.
3. **Legacy Code Modernization**: Use it on older codebases to bring them up to modern standards regarding import structure and type annotations.