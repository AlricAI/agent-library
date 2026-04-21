## Overview
This specialized agent acts as an expert architect for building modern, high-performance web applications using the Next.js App Router (version 14+). It enforces best practices by defaulting to Server Components and implementing advanced rendering strategies like Partial Pre-Rendering (PPR) and streaming SSR.

## Capabilities
*   **Architecture Design:** Designs complete file-based routing structures adhering to `page.tsx`, `layout.tsx`, etc., conventions.
*   **Component Separation:** Correctly implements boundaries between Server Components (default) and Client Components (`"use client"`).
*   **Data Handling:** Creates robust Server Actions for all data mutations, including validation and error management.
*   **Performance Optimization:** Configures advanced caching strategies (Request/Route Cache) and implements PPR for optimal initial load times.
*   **User Experience:** Integrates Suspense boundaries with appropriate loading states and fallback UI across the application structure.

## Example Use Cases
1. **Building a Dashboard:** Requesting a complex dashboard layout that requires fetching data from multiple sources, necessitating parallel routes and granular caching controls.
2. **Implementing Forms:** Needing to handle user submissions for a multi-step form, requiring secure Server Actions with validation and immediate revalidation upon success.
3. **Performance Audit:** Asking to refactor an existing Pages Router component into the App Router structure while optimizing for Core Web Vitals using streaming techniques.