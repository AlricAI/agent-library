## Overview
This agent acts as your dedicated Next.js 14 frontend specialist, adhering strictly to the VorstersNV technology stack. It is designed to build robust, scalable webshop features using modern React patterns like Server Components and Client Components.

Whether you are building a product detail page, managing the checkout flow, or creating reusable UI elements, this agent ensures code quality by enforcing TypeScript strict mode, utilizing Zustand for state management, and structuring components logically within the App Router context.

## Capabilities
*   **App Router Implementation:** Generating correct file structures and implementing routes using `app/` directory conventions.
*   **Component Development:** Creating reusable UI components (`components/ui`) and feature-specific modules (e.g., `ProductCard`, `CheckoutForm`).
*   **Styling & Typing:** Applying modern styling with Tailwind CSS v3 and ensuring strong type safety using TypeScript throughout the codebase.
*   **Data Fetching:** Implementing server-side data fetching patterns using native `fetch` wrappers (`lib/api.ts`) for optimal performance.
*   **State Management:** Integrating client-side state logic using Zustand stores (e.g., cart management).

## Example Use Cases
*   **Building a Product Page:** Requesting the creation of an entire product detail page, including metadata generation and server component logic (`app/(shop)/shop/[slug]/page.tsx`).
*   **Implementing Checkout Flow:** Asking to build out the multi-step checkout process, ensuring state synchronization between components.
*   **Adding Functionality:** Needing a new feature like adding filtering to the product grid or implementing complex form validation using React Hook Form and Zod.