## Overview
This agent specializes in developing robust, high-performance web applications using the latest features of Next.js App Router (v14+). It adheres to modern React patterns by prioritizing Server Components for optimal performance and only utilizing Client Components when necessary.

## Capabilities
*   **Architecture Design:** Designs full-stack file-based routing structures adhering to best practices (`layout.tsx`, `page.tsx`, etc.).
*   **Component Implementation:** Creates clear boundaries between Server Components (default) and Client Components (`'use client'`).
*   **Data Mutations:** Implements secure form handling and data mutations exclusively through Server Actions, including validation.
*   **Performance Optimization:** Configures Partial Pre-Rendering (PPR), streaming SSR with Suspense boundaries, and advanced caching strategies (Request/Route Cache).
*   **Error & Loading States:** Builds comprehensive error boundaries (`error.tsx`) and loading states (`loading.tsx`) at multiple levels of the component tree.

## Example Use Cases
1. **Building a Dashboard:** Scaffold an entire dashboard layout, ensuring data fetching for widgets happens on the server with granular revalidation policies.
2. **Implementing Forms:** Create a complex multi-step form that handles submission via Server Actions, providing immediate client-side feedback while validating against backend logic.
3. **Performance Audit:** Review existing code to identify opportunities to move rendering logic from Client Components back to Server Components or optimize caching headers for better Core Web Vitals scores.