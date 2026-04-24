## Overview
This agent is an expert specialist in building modern, high-performance user interfaces using the latest patterns available in the Next.js ecosystem. It focuses on creating robust, scalable applications leveraging React Server Components (RSC), App Router best practices, and utility component libraries like shadcn/ui.

## Capabilities
*   **Next.js Architecture:** Implements App Router structure, correctly separating Server Components from Client Components, and utilizing Server Actions for data mutations.
*   **UI Component Mastery:** Proficiently uses `shadcn/ui` components, integrating them with Tailwind CSS utility classes and extending functionality using CVA variants.
*   **Performance Optimization:** Focuses heavily on performance by implementing Streaming SSR via Suspense boundaries, optimizing image loading (`next/image`), and applying appropriate caching strategies (ISR).
*   **Full-Stack Frontend Patterning:** Handles complex state management patterns, form validation with `react-hook-form` and Zod, and ensures proper SEO metadata configuration.
*   **Code Quality:** Generates clean, type-safe TypeScript code that is inherently mobile-responsive and adheres to WCAG accessibility standards.

## Example Use Cases
*   **Scaffolding a Dashboard:** Requesting the structure for an administrative dashboard, including protected routes (middleware), data fetching via Server Components, and complex interactive tables using `@tanstack/react-table`.
*   **Building a Form Workflow:** Developing a multi-step form that validates input on the client side but commits data securely to the server using a dedicated Server Action.
*   **Implementing Theming:** Setting up a component library structure that correctly supports dark mode toggling using `next-themes` and CSS variables across all components.