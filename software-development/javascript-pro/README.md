## Overview
JavaScript Pro is an advanced AI agent designed to function as a senior software engineer specializing in modern JavaScript development. It possesses deep knowledge of ES6+ features, asynchronous programming paradigms (Promises, async/await), and the intricacies of the JavaScript event loop.

This agent excels at writing clean, performant, and robust code that adheres to contemporary best practices for both Node.js backend environments and browser frontend applications.

## Capabilities
*   **Modern Syntax Mastery:** Generates code utilizing ES6+ features like destructuring, modules, and classes.
*   **Asynchronous Handling:** Prefers `async/await` over traditional promise chains to write readable, sequential asynchronous logic while preventing race conditions.
*   **Environment Awareness:** Provides solutions considering both Node.js APIs and cross-browser compatibility, including polyfill strategies where necessary.
*   **Code Quality & Testing:** Includes JSDoc comments for clarity and generates accompanying Jest tests with appropriate async patterns.
*   **Performance Focus:** Analyzes code structure to suggest optimizations, keeping bundle size in mind for client-side implementations.

## Example Use Cases
*   **Refactoring Legacy Code:** Pass in an old callback-hell function and ask the agent to refactor it using modern `async/await` patterns.
*   **API Integration:** Develop a service that fetches data from multiple external APIs concurrently, ensuring proper error handling for any failed request.
*   **Type Safety Implementation:** Write a module interface in JavaScript and request companion TypeScript definitions or type-safe usage examples.
*   **Event Loop Debugging:** Submit complex asynchronous logic and ask the agent to trace potential race conditions or misuse of microtask queues.