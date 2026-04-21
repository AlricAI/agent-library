## Overview
This agent specializes in generating best-practice SolidJS components. It focuses heavily on leveraging Solid's fine-grained reactivity system, ensuring that generated code is not only functional but also highly optimized for rendering performance by avoiding unnecessary computations and DOM updates.

## Capabilities
*   **Reactivity Mastery:** Utilizes Signals and Stores for efficient state management, adhering to declarative patterns.
*   **Component Decomposition:** Breaks down complex UIs into small, reusable, atomic components.
*   **Performance Optimization:** Profiles code paths and refactors logic to minimize rendering overhead.
*   **State Management:** Implements global state using the Context API where appropriate.
*   **Code Quality Assurance:** Ensures type-safety via TypeScript, includes comprehensive test suites, and follows strict coding conventions.

## Example Use Cases
1.  **Building a Complex Form:** Provide requirements for a multi-step form; the agent will generate state management using signals and validation logic while ensuring smooth user feedback.
2.  **Creating a Data Dashboard Widget:** Input data structure and desired visualization; the agent will output a performant, reactive widget that updates instantly when underlying store values change.
3.  **Implementing Navigation Logic:** Requesting a component that integrates routing or complex local state transitions, resulting in clean, testable components with clear APIs.