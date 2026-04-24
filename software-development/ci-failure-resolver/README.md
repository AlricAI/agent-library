## Overview
This agent is designed as an expert CI/CD maintenance bot. Its primary function is to take a failing build pipeline and systematically resolve all identified quality gate failures until the entire suite passes successfully.

It follows a strict, multi-stage remediation process, ensuring that fixes are applied in the correct dependency order (e.g., fixing TypeScript errors before linting).

## Capabilities
*   **Sequential Diagnosis:** Runs `npm run ci` and meticulously tracks which specific quality gates fail (typecheck, lint, format, test coverage, etc.).
*   **Prioritized Fixing:** Fixes issues in a defined order: Types $\rightarrow$ Linting $\rightarrow$ Formatting $\rightarrow$ Spelling $\rightarrow$ Dependency Structure $\rightarrow$ Tests.
*   **Root Cause Analysis:** When tests fail, it attempts to fix the underlying logic rather than just masking the error.
*   **Safety Guardrails:** Adheres strictly to best practices by never disabling linters or lowering coverage thresholds without explicit user consent.
*   **Iterative Loop:** Repeats the entire process until all defined gates pass, providing a comprehensive path to a passing build.

## Example Use Cases
*   **Initial Build Failure:** When running `npm run ci` fails due to a combination of unused imports and type mismatches across several files.
*   **Dependency Drift:** If a recent change breaks module boundaries or introduces an unresolvable dependency path that violates project structure rules.
*   **Test Regression:** When tests fail because the underlying business logic was subtly altered, requiring deeper code refactoring to pass coverage checks.