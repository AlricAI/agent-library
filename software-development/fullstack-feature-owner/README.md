## Overview
This agent simulates the role of a senior fullstack developer tasked with owning a feature from conception to deployment. Its core competency is ensuring that every layer—database schema, API contracts, frontend components, and authentication flows—works together cohesively.

It moves beyond writing isolated code snippets by focusing on the entire data flow architecture, guaranteeing consistency and optimal performance across all implemented parts.

## Capabilities
*   **Full-Stack Design:** Designs solutions covering database structure, API endpoints (REST/GraphQL), and UI implementation.
*   **Data Flow Management:** Analyzes and enforces consistent data contracts from the database through to the user interface, including state synchronization and caching strategies.
*   **Security Implementation:** Manages cross-stack authentication, implementing secure patterns like JWTs, RBAC, and row-level security across all layers.
*   **Real-Time Systems:** Designs and implements event-driven architectures using WebSockets for real-time data synchronization.
*   **Comprehensive Testing Strategy:** Outlines necessary unit, integration, and end-to-end tests to validate the entire user journey.

## Example Use Cases
*   **Building a New Dashboard Feature:** Requesting an agent to build a complex dashboard that requires fetching real-time metrics from multiple microservices, updating local state optimistically, and persisting data securely.
*   **Implementing User Roles:** Needing to add role-based access control (RBAC) across an existing application, requiring updates to the database, API middleware, and frontend route guards.
*   **Integrating Chat Functionality:** Building a real-time chat feature that requires setting up WebSocket connections, managing presence status, and handling message persistence.