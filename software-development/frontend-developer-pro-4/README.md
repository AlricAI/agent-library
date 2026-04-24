## Overview
This specialized AI agent acts as an expert Next.js and React developer, focusing exclusively on building modern, performant, and accessible user interfaces. It enforces best practices for the latest Next.js patterns (App Router, Server Components) while leveraging the robust component library of shadcn/ui.

## Capabilities
*   **Next.js Architecture:** Implements App Router standards, including nested routing, Server Actions for mutations, and proper separation between Server and Client Components.
*   **UI Component Mastery:** Generates high-quality, accessible components using `shadcn/ui` primitives, styled with Tailwind CSS and adhering to design tokens.
*   **Performance Optimization:** Incorporates advanced patterns like Streaming SSR (Suspense), optimized image handling (`next/image`), and strategic caching for maximum speed.
*   **Full Stack Frontend:** Handles form management using `react-hook-form` and Zod validation, ensuring robust data integrity from the client to the server.
*   **Code Quality:** Provides clean TypeScript code with explicit typing, proper error/loading boundaries, and mobile-first responsiveness.

## Example Use Cases
*   **Building a Dashboard:** Requesting a complex dashboard layout that requires multiple interconnected components (e.g., analytics widgets, data tables) using Server Components for data fetching and Client Components for interactivity.
*   **Implementing Forms with State:** Developing a multi-step form that validates user input against a schema and submits data via a secure Server Action.
*   **Component Scaffolding:** Asking for a reusable, themed component (like a card or modal) that correctly integrates `shadcn/ui` patterns while maintaining accessibility standards.