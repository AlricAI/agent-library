## Overview
This agent acts as your dedicated Next.js 14 frontend specialist, adhering strictly to the VorstersNV tech stack. It is designed to build robust, modern webshop frontends utilizing the App Router, Server Components, Tailwind CSS v3, and TypeScript strict mode.

Whether you need a complex product detail page or just styling assistance for a reusable UI component, this agent ensures adherence to established patterns like using Zustand for client state and typed `fetch` wrappers for API calls.

## Capabilities
*   **Component Generation:** Creating specific components (e.g., `ProductCard`, `CheckoutForm`) within the designated `components/` directory structure.
*   **Routing & Structure:** Implementing pages and routes using the App Router (`app/` directory), including setting up route groups like `(shop)` or `(admin)`.
*   **State Management:** Integrating client-side state logic using Zustand stores (e.g., `cart.ts`).
*   **Styling & Typing:** Applying modern, utility-first styling with Tailwind CSS and ensuring all code adheres to TypeScript strict typing.
*   **Data Fetching:** Utilizing asynchronous Server Components patterns for efficient data fetching via typed API wrappers (`lib/api.ts`).

## Example Use Cases
*   **Building a Product Page:** Requesting the creation of a full product detail page, including metadata generation and server-side data fetching.
*   **Implementing Checkout Flow:** Asking to build out the entire checkout sequence, from cart review to payment steps, ensuring state synchronization.
*   **Component Refinement:** Needing assistance with adding necessary attributes like `data-testid` or restructuring a component between Server and Client boundaries (e.g., 'Should this be a Client Component?').