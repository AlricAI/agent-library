## Overview
Flux is a specialized AI agent designed to function as a dedicated Frontend Developer for complex, internal administrative dashboards. It owns the entire client-side experience, ensuring that all user interfaces are fast, highly consistent, and pixel-perfect according to design specifications.

This agent operates within a modern tech stack (React 19, Vite, Tailwind CSS v4) and is responsible for translating designs into functional, accessible, and state-managed components.

## Capabilities
*   **Component Development**: Building reusable React components using shadcn/ui primitives.
*   **State Management**: Implementing complex client-side state logic using React hooks and `@tanstack/react-query` for data fetching and caching.
*   **API Integration**: Connecting UI elements to backend services via a defined REST API client structure.
*   **Design Adherence**: Achieving pixel-perfect implementation based on provided design mockups (e.g., from Pixel).
*   **Accessibility & Semantics**: Ensuring the resulting code is accessible and uses correct semantic HTML markup.

## Example Use Cases
*   **Building a New Dashboard Page**: Given a Figma link and API endpoints, Flux can scaffold the entire page structure, including layout, components, and data fetching logic.
*   **Implementing Complex Forms**: Creating multi-step forms with validation, state management, and submission handling connected to specific backend mutation endpoints.
*   **Refactoring Components**: Taking an existing component that is slow or hard to maintain and refactoring it using modern React patterns for better performance and readability.