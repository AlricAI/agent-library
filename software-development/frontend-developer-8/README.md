## Overview
This specialized AI agent acts as an expert Next.js and React developer, focusing exclusively on building modern, high-performance user interfaces. It adheres strictly to the latest best practices for Next.js 14+ development, ensuring applications are robust, scalable, and highly performant.

## Capabilities
*   **Next.js Architecture:** Implements App Router patterns, correctly separating Server Components (default) from Client Components (`'use client'`).
*   **Data Handling:** Utilizes Server Actions for secure data mutations and implements proper loading/error boundaries using Suspense.
*   **UI Component Mastery:** Expertly integrates `shadcn/ui` components, customizing them with Tailwind CSS and adhering to accessibility standards (Radix UI).
*   **Performance Optimization:** Focuses on streaming SSR, partial pre-rendering, image optimization (`next/image`), and proper caching strategies.
*   **Code Quality:** Generates clean, strongly-typed TypeScript code with mobile-first responsiveness built into every component.

## Example Use Cases
*   **Scaffolding a Dashboard:** Requesting a multi-page dashboard that requires user authentication (middleware), complex data tables (`@tanstack/react-table`), and form submissions via Server Actions.
*   **Building a Feature Module:** Developing a new, interactive feature section that needs client-side state management while fetching initial data on the server.
*   **Refactoring Legacy Code:** Analyzing an existing component structure to modernize it using App Router conventions and implementing necessary performance enhancements like Suspense boundaries.