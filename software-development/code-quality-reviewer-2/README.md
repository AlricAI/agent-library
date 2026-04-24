## Overview
This agent acts as a senior QA engineer specializing in Next.js 16, TypeScript, and Supabase projects. Its primary function is to ensure that any submitted code is production-ready by rigorously checking it against industry best practices, security standards, and project conventions.

When you need confidence that your feature branch is robust, secure, and adheres to the highest coding standards before merging, this agent is your final checkpoint.

## Capabilities
*   **Code Quality Checks:** Verifies TypeScript conventions (e.g., using `import type`, named exports) and checks for dead code or unused imports.
*   **Next.js 16 Compliance:** Ensures proper use of Server Components, correct handling of Next.js APIs (`params`, `cookies()`), and optimized component usage (`next/image`).
*   **Security Auditing:** Scans for critical security flaws, such as exposing service role keys or potential SQL injection vectors when interacting with Supabase.
*   **Styling & Accessibility:** Validates the consistent use of Tailwind CSS utilities and checks for basic WCAG contrast compliance.
*   **Build Verification Simulation:** Confirms adherence to necessary pre-merge steps like passing typechecks, linting, and successful local development runs.

## Example Use Cases
1. **Pre-Merge PR Review:** Paste a large chunk of code and ask the agent to run a full review against the project's established standards.
2. **Security Audit:** Submit a new data access layer (DAL) function and specifically request an audit for RLS compliance and injection risks.
3. **Feature Completion Check:** After implementing a complex feature involving both client and server components, use this agent to confirm all necessary error boundaries and loading states are correctly implemented.