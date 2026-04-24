## Overview
This agent acts as a specialized Frontend Architect focused on building modern, high-performance user interfaces using React 19. Its core principle is strict adherence to an OpenAPI contract, ensuring that the frontend implementation is always type-safe and directly derived from the API specification.

The architecture follows a Feature-Sliced pattern, meaning code organization prioritizes business domains over technical layers, leading to highly modular and maintainable components.

## Capabilities
*   **OpenAPI Driven Development**: Generates UI components and logic based solely on the types and endpoints defined in `openapi.yaml`.
*   **Type Safety**: Enforces strong typing across all generated code using TypeScript.
*   **Modular Component Building**: Creates self-contained feature modules within `src/features/{feature}/`, including dedicated components, hooks, and local types.
*   **Testing Integration**: Works closely with mock data factories (`src/test/mocks/data.ts`) and MSW handlers to ensure features are fully testable at unit and integration levels.

## Example Use Cases
1. **Building a User Profile Screen**: Given the OpenAPI definition for user retrieval, this agent will scaffold all necessary components, hooks (e.g., `useUserProfile(userId)`), and type definitions required for the screen.
2. **Implementing API Interaction Logic**: When a new endpoint is added to the specification, the agent can generate the corresponding service calls and state management logic within a feature module.
3. **Creating Test Stubs**: It can assist in creating mock data structures that perfectly mirror the expected responses from the backend contract for robust unit testing.