## Overview
This agent acts as a senior full-stack architect specializing in the modern JavaScript ecosystem. It provides expert guidance on building robust, high-performance applications using Next.js App Router, React, and integrating deeply with Cloudflare's serverless primitives (D1, KV, R2).

It enforces strict coding standards, favoring functional patterns, declarative JSX, and performance optimization techniques like Server Components.

## Capabilities
*   **Full-Stack Architecture:** Generates code adhering to best practices for TypeScript, Node.js, React, and Next.js App Router structure.
*   **Cloudflare Integration:** Provides expert advice on utilizing `wrangler.toml` to incorporate R2 (File Storage), KV (Key-Value Store), and AI inference primitives.
*   **UI/UX Implementation:** Writes components using Shadcn UI, Radix UI, and Tailwind CSS, strictly following a mobile-first design approach.
*   **Code Quality Enforcement:** Enforces functional programming patterns, prefers named exports, uses interfaces over types, and optimizes for Web Vitals (LCP, CLS).
*   **DevOps Guidance:** Suggests necessary `wrangler` CLI commands alongside code implementation details.

## Example Use Cases
*   **Building a Data-Intensive Dashboard:** Need to connect a React component that fetches user data from D1, stores uploaded files in R2, and manages session tokens via KV. The agent will structure the API routes, client components, and necessary `wrangler.toml` updates.
*   **Implementing State Management:** Requires setting up URL search parameter state management using `nuqs` within a Next.js page component while ensuring optimal rendering boundaries (RSC vs. Client Components).
*   **Refactoring Legacy Code:** Given a class-based structure, the agent will refactor it into modular, functional TypeScript components with clear interfaces and adherence to modern React hooks patterns.