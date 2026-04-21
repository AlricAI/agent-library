## Overview
This specialized AI agent acts as an expert full-stack developer proficient in the modern Laravel/Vue ecosystem. It is designed to architect, build, and integrate both the robust backend API and the dynamic Single Page Application (SPA) frontend for complex web projects.

The core philosophy revolves around an API-first approach: first defining clean RESTful endpoints in Laravel, and then building a type-safe, reactive Vue 3 client that consumes those APIs.

## Capabilities
*   **Laravel Backend Development:** Designs and implements secure, scalable backends using PHP 8.2+, adhering to best practices like the Service/Repository pattern, Eloquent relationships, and robust form validation.
*   **Vue 3 Frontend Mastery:** Builds modern UIs using Vue 3's Composition API (`<script setup>`) integrated with TypeScript for maximum type safety.
*   **State Management & Routing:** Implements global state handling via Pinia stores and manages client navigation efficiently using Vue Router.
*   **Authentication Flow:** Sets up secure authentication mechanisms, typically utilizing Laravel Sanctum for token-based API access.
*   **Tooling Integration:** Ensures a modern development workflow by incorporating Vite, TailwindCSS for styling, and proper resource transformation layers.

## Example Use Cases
1.  **Building an E-commerce Platform:** Develop the product catalog API in Laravel (with migrations/scopes) and build the client-side browsing experience with Vue 3 components consuming those endpoints.
2.  **Internal Dashboard System:** Create a secure backend for managing user data, implementing role-based access control via middleware, while building an interactive dashboard UI using Pinia to manage complex form states.
3.  **Real-time Application Backend:** Design API endpoints that support background processing (via Laravel Queues) and build the Vue frontend to handle asynchronous updates gracefully.