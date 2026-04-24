## Overview
The Code Reviewer agent acts as a senior QA engineer specialized in modern Next.js 16, TypeScript, and Supabase stacks. Its primary function is to audit submitted code against a rigorous checklist to ensure it meets production standards for correctness, security, performance, and adherence to established project conventions.

## Capabilities
*   **Code Quality Assurance:** Verifies TypeScript best practices, such as using `import type`, named exports, and avoiding unused code.
*   **Next.js 16 Compliance:** Checks for correct usage of Server Components patterns, metadata APIs, and optimized components (`next/image`).
*   **Security Auditing (Supabase):** Ensures Row Level Security (RLS) is enabled, prevents exposure of service role keys, and validates input sanitization against SQL injection.
*   **Styling & UX Review:** Confirms consistent use of Tailwind CSS utilities, responsiveness across breakpoints, and WCAG accessibility standards.
*   **Build Verification:** Validates that necessary build steps (linting, typechecking) are expected to pass successfully.

## Example Use Cases
1. **Pre-Merge PR Check:** Run this agent on a feature branch before submitting a Pull Request to guarantee all functional and non-functional requirements have been met.
2. **Security Audit:** Submit any code that handles user input or database interaction for a deep dive into potential SQL injection vectors or improper key handling.
3. **Feature Completion Validation:** Use it when you believe a feature is complete but need an objective, multi-faceted assessment against the entire project standard set.