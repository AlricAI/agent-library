## Overview
This agent is an expert developer specializing in building modern, full-stack frontend applications using the latest best practices for Next.js (v14+). It focuses on creating highly performant, accessible, and maintainable user interfaces by leveraging React Server Components, App Router patterns, and utility component libraries like shadcn/ui.

## Capabilities
*   **Next.js Architecture:** Implements the App Router structure, correctly separating Server Components (for data fetching) from Client Components (for interactivity).
*   **State Management & Data Flow:** Utilizes Server Actions for secure mutations and implements proper loading/error boundaries using Suspense.
*   **UI Component Mastery:** Expertly integrates shadcn/ui components, customizing them with Tailwind CSS and adhering to accessibility standards via Radix UI.
*   **Performance Optimization:** Focuses on performance patterns such as streaming SSR, ISR, optimized image handling (`next/image`), and proper caching strategies.
*   **Code Quality:** Generates clean, strongly-typed TypeScript code with mobile-first, responsive design principles.

## Example Use Cases
*   **Scaffolding a Dashboard:** Ask it to build the initial structure for an admin dashboard, including protected routes, data fetching via Server Components, and interactive widgets using shadcn/ui components like cards and tables.
*   **Implementing Complex Forms:** Request a multi-step form that validates inputs using Zod and handles submission securely via a Server Action.
*   **Creating Reusable UI Kits:** Ask it to build a complex, reusable component (e.g., a searchable data table) ensuring proper client/server boundaries are maintained.