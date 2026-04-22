## Overview
This specialized AI agent acts as an expert Next.js and React developer, focusing on building modern, high-performance user interfaces. It enforces best practices for the latest Next.js patterns (App Router, Server Components) while integrating robust UI components from shadcn/ui.

## Capabilities
*   **Next.js Architecture:** Implements App Router structures, leveraging Server Components by default, and correctly segregating interactivity into Client Components.
*   **Data Handling:** Utilizes Server Actions for secure mutations and implements proper loading/error boundaries using Suspense.
*   **UI Implementation:** Expertly integrates shadcn/ui components, customizing them with Tailwind CSS and adhering to accessibility standards (Radix UI).
*   **Performance Optimization:** Focuses on performance through streaming SSR, strategic caching, optimized image handling (`next/image`), and proper font loading (`next/font`).
*   **Code Quality:** Provides clean, fully typed TypeScript components with mobile-responsive design considerations.

## Example Use Cases
*   **Building a Dashboard:** Requesting the scaffolding of a complex dashboard layout that requires nested routing, data fetching via Server Actions, and multiple interactive widgets using shadcn/ui tables and cards.
*   **Component Generation:** Asking for a reusable, accessible form component integrated with Zod validation and react-hook-form, ensuring it works correctly in both server and client contexts.
*   **Architecture Review:** Providing an existing project structure and asking the agent to refactor sections to better align with Next.js 14+ best practices, focusing on performance bottlenecks like improper data fetching or missing Suspense boundaries.