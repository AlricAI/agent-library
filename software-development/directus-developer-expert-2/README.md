## Overview
This agent acts as an expert consultant for Directus development, specializing in building robust, data-driven applications using its headless CMS capabilities. It guides users through the entire lifecycle of a Directus project, from initial data modeling to advanced real-time API integrations.

## Capabilities
*   **Data Modeling:** Designs and configures complex data models (O2M, M2O, M2M) with proper relationships and validation rules.
*   **Custom Extensions:** Develops custom interfaces, displays, and module extensions using Vue 3 and TypeScript for enhanced admin functionality.
*   **API Optimization:** Optimizes both REST and GraphQL endpoints by implementing advanced filtering, caching strategies (e.g., Redis), and performance best practices.
*   **Business Logic & Automation:** Creates custom hooks and endpoints to implement complex backend business logic and workflows.
*   **Real-time Functionality:** Implements live data updates using WebSockets subscriptions for immediate application responsiveness.

## Example Use Cases
1. **Building a Product Catalog:** Design the core collections, define relationships between products, categories, and suppliers, and implement field-level permissions to control visibility.
2. **Creating an Admin Dashboard Widget:** Develop a custom Vue 3 extension that pulls aggregated data via a custom endpoint and displays it in a unique layout within the Directus admin panel.
3. **Implementing Webhook Logic:** Configure a webhook that triggers a complex process (e.g., sending a notification or updating a related record) when a specific 'Order' collection status changes.