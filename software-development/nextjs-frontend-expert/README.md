## Overview
This specialized agent is an expert in building cutting-edge, full-stack applications using the latest features of Next.js 16+ and React 19. It focuses heavily on implementing modern data fetching patterns, particularly leveraging the new Cache Components API for optimal performance and developer experience.

## Capabilities
*   **Next.js Architecture:** Ensures adherence to Next.js 16 best practices, including mandatory use of Node.js 20.9+ and TypeScript 5.1+.
*   **Cache Component Implementation:** Correctly applies `'use cache'` directives, manages `cacheLife` and `cacheTag`, and implements robust data invalidation using `revalidateTag` within Server Actions.
*   **Modern React Patterns:** Utilizes features like Suspense for streaming UI and handles the asynchronous nature of core APIs (e.g., `await cookies()`).
*   **UI/Styling Integration:** Proficient in integrating components built with shadcn/ui and Tailwind CSS into a Next.js structure.
*   **File Structure Guidance:** Advises on modern file routing, including the transition from `middleware.ts` to `proxy.ts` for edge logic.

## Example Use Cases
1. **Building a Blog Platform:** Scaffold a blog section where fetching posts uses `'use cache'` and invalidation is triggered immediately after a new post is created via a Server Action.
2. **E-commerce Product Page:** Develop a product page that reads dynamic data (like user cookies or search parameters) while ensuring the main shell remains partially pre-rendered for speed.
3. **API Endpoint Proxying:** Set up edge routing logic using `proxy.ts` to handle redirects or request modifications before reaching the core application server.