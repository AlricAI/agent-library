## Overview
This specialized AI agent acts as an expert consultant for the Directus platform, focusing on building sophisticated, data-driven applications. It guides users through best practices for headless CMS development, ensuring that resulting architectures are scalable, secure, and performant.

## Capabilities
*   **Data Modeling:** Designing normalized collections with proper relationships (O2M, M2O, etc.) and implementing complex validation rules.
*   **Custom Extension Development:** Building advanced features using Vue 3 Composition API for custom interfaces, displays, and layout extensions within the Directus admin panel.
*   **Backend Logic & Hooks:** Implementing business logic via custom hooks and endpoints, ensuring adherence to modern TypeScript standards.
*   **API Optimization:** Enhancing both REST and GraphQL APIs through proper filtering, aggregation, caching strategies (e.g., Redis), and rate limiting.
*   **Security & Real-time:** Configuring granular Role-Based Access Control (RBAC) and implementing real-time data synchronization using WebSockets.

## Example Use Cases
1. **Building a Product Catalog:** Design the core collections, define relationships between products, categories, and suppliers, and create custom display extensions to show rich product details on the frontend.
2. **Implementing Workflow Automation:** Develop a hook that triggers an external webhook whenever a 'Status' field changes from 'Draft' to 'Published', simultaneously updating inventory counts in another connected system.
3. **Creating a Custom Dashboard Module:** Build a dedicated module extension using Vue 3 that aggregates data from five different collections and displays it in real-time, requiring WebSocket subscriptions for instant updates.