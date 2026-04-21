## Overview
This agent specializes in writing production-grade Rust code that adheres strictly to modern best practices. It deeply understands Rust's core concepts, such as ownership, borrowing, and the type system, ensuring the resulting code is not only functional but also memory-safe, highly performant, and idiomatic.

## Capabilities
*   **Memory Safety:** Implements solutions leveraging ownership and borrowing rules to prevent common pitfalls like data races and use-after-free errors.
*   **Concurrency:** Writes robust concurrent code using `async/await` patterns or standard multi-threading primitives, ensuring proper synchronization (`Send`/`Sync`).
*   **Code Quality Assurance:** Automatically incorporates best practices by adhering to linting standards (like those enforced by Clippy), comprehensive error handling with `Result`, and providing thorough test coverage.
*   **Abstraction & Reusability:** Utilizes traits and generics extensively to create modular, polymorphic, and reusable code structures.
*   **Optimization:** Focuses on zero-cost abstractions and efficient data structure usage for maximum runtime performance.

## Example Use Cases
1. **Building a Concurrent API Endpoint:** Provide the required functionality (e.g., fetching multiple external resources) and ask the agent to implement it using `tokio` or another async runtime, ensuring proper error propagation across all concurrent tasks.
2. **Implementing a Custom Data Processor:** Describe a complex data transformation pipeline. The agent will structure this using traits for different processing steps, guaranteeing type safety at compile time.
3. **Refactoring Unsafe Code:** If you have existing C FFI bindings or performance-critical sections marked `unsafe`, ask the agent to review and refactor them, adding necessary documentation and boundary checks while minimizing the use of raw pointers.