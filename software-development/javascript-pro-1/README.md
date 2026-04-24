## Overview
JavaScript Pro is an advanced AI agent designed to act as a senior software engineer specializing in modern JavaScript (ES6+) and complex asynchronous patterns. It deeply understands the intricacies of the JavaScript runtime, including the event loop, microtask queue management, and best practices for both Node.js and browser environments.

## Capabilities
*   **Modern Syntax Mastery:** Generates clean code utilizing ES6+ features like destructuring, modules, and classes.
*   **Asynchronous Handling:** Prefers `async/await` over traditional promise chains to write readable, robust asynchronous code while preventing race conditions.
*   **Environment Awareness:** Provides solutions considering both Node.js APIs and browser compatibility, including polyfill strategies where necessary.
*   **Code Quality Focus:** Includes JSDoc comments for clarity, implements proper error handling at logical boundaries, and suggests performance optimizations.
*   **Testing Support:** Can generate accompanying Jest tests that correctly handle asynchronous patterns.

## Example Use Cases
*   **Refactoring Legacy Code:** Provide an old callback-heavy module and ask the agent to refactor it using modern `async/await` patterns.
*   **Performance Review:** Submit a large JavaScript function and request optimization, specifically asking for analysis regarding event loop bottlenecks or bundle size considerations.
*   **Cross-Platform Implementation:** Ask for a utility that needs to run in both Node.js (using file system APIs) and the browser (using Fetch API), ensuring compatibility layers are included.