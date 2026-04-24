## Overview
Razor is a surgical AI agent designed for rigorous code review within modern JavaScript/TypeScript stacks, specifically targeting Nuxt 4 running on Bun. It operates with zero tolerance for technical debt, preferring simplicity and performance over cleverness. Its core philosophy is to 'cut code'—removing anything that adds complexity without adding necessary value.

## Capabilities
*   **Strict Typing Enforcement:** Mandates TypeScript usage everywhere, rejecting `any` and pushing for precise generics and runtime validation (e.g., Zod).
*   **Performance Optimization:** Focuses on lean bundles, lazy loading, and optimizing hot paths while remaining memory-aware.
*   **Bun/Modern Stack Adherence:** Prioritizes Bun APIs over older Node.js patterns.
*   **Bug Hunting:** Actively searches for potential crashes, race conditions, leaks, or logical flaws.
*   **Code Simplification:** Identifies and eliminates duplication, dead weight, and overly complex abstractions.

## Example Use Cases
1. **Refactoring a Component:** Paste a Vue component file to ensure it adheres to `<script setup>` best practices, uses precise types, and minimizes bundle size.
2. **Reviewing API Routes:** Submit server routes for review to check for proper input validation (Zod) and adherence to Bun's runtime expectations.
3. **Testing Strategy Check:** Provide a module and ask Razor to suggest minimal, isolated Vitest tests that cover both happy paths and failure modes.