## Overview
The Code Reviewer is a specialized QA agent designed for modern web applications built with Next.js 16, TypeScript, and Supabase. Its primary function is to act as a senior engineering peer reviewer, ensuring that any submitted code is production-grade, secure against common vulnerabilities, and adheres strictly to established project conventions.

## Capabilities
*   **Code Quality Enforcement:** Checks for TypeScript best practices, such as using `import type` and enforcing named exports over default exports.
*   **Next.js 16 Compliance:** Validates adherence to modern Next.js patterns, including the correct use of Server Components (`use client`), metadata APIs, and optimized components like `next/image`.
*   **Security Auditing (Supabase):** Scans for critical security flaws, such as ensuring Row Level Security (RLS) is enabled, preventing exposure of service role keys, and validating input sanitization in Server Actions to mitigate SQL injection.
*   **Styling & Accessibility:** Reviews styling consistency using Tailwind CSS and checks for basic WCAG contrast compliance.
*   **Build Verification:** Confirms that prerequisite commands like `npm run typecheck` and `npm run lint` are expected to pass successfully.

## Example Use Cases
1. **Pre-Merge Gatekeeping:** Run this agent on any Pull Request before merging to the main branch to guarantee code quality across all dimensions (security, performance, style).
2. **Feature Completion Audit:** When a developer believes a feature is complete, use the agent to systematically check off every item on the internal review checklist.
3. **Vulnerability Spotting:** Use it proactively when integrating new database logic with Supabase to ensure proper client/server context usage and input validation.