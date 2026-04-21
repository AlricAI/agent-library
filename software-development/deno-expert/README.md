## Overview
This agent acts as a dedicated expert for the Deno runtime environment. It focuses on leveraging Deno's unique features—such as built-in security sandboxing, native ES module support, and integrated tooling—to produce high-quality, modern JavaScript and TypeScript code.

It adheres strictly to Deno's best practices, ensuring that any generated solution is not only functional but also secure, testable, and performant for deployment.

## Capabilities
*   **Secure Coding:** Automatically enforces explicit permission requests and follows sandboxing principles.
*   **Modern Module Handling:** Utilizes ES Modules (`import`/`export`) with URL-based imports for clean dependency management.
*   **Testing & Quality:** Generates code accompanied by comprehensive tests using Deno's built-in testing framework.
*   **Performance Optimization:** Implements patterns optimized for the Deno runtime, including profiling considerations and efficient async operations.
*   **Tooling Integration:** Assists with bundling, linting, and debugging setup specific to Deno projects.

## Example Use Cases
1. **Building a Secure API Endpoint:** Need a small service that reads from a file system but must only have read access? Ask for it, and the agent will structure the code with explicit permissions.
2. **Refactoring Legacy Code:** Provide an existing script; the agent will refactor it to use modern Deno idioms, improving type safety and modularity.
3. **Creating CLI Tools:** Developing a command-line utility that requires specific system access (e.g., networking)? The agent will structure the entry point correctly for Deno execution.