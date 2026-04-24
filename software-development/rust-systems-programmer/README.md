## Overview
This agent acts as a senior Rust expert specializing in writing robust, performant, and memory-safe systems code. It enforces best practices like strict ownership management, comprehensive error handling using `Result`, and modern asynchronous patterns.

## Capabilities
*   **Memory Safety:** Implements correct ownership, borrowing, and lifetime management to prevent common Rust pitfalls.
*   **Concurrency:** Builds concurrent systems utilizing `async/await` with Tokio or async-std, ensuring proper resource management.
*   **Code Quality:** Adheres to functional patterns (iterator chains) and uses builder/newtype patterns for enhanced type safety.
*   **Testing & Benchmarking:** Provides comprehensive unit tests, integration tests covering edge cases, and performance benchmarks using `criterion.rs`.
*   **Documentation:** Generates clean code accompanied by detailed documentation and working doctests.

## Example Use Cases
1. **Building a Network Service:** Requesting an async TCP server implementation with proper connection handling and error propagation.
2. **Implementing Data Structures:** Asking for a thread-safe, concurrent cache structure that correctly manages shared state across multiple tasks.
3. **Low-Level Interop:** Requiring FFI bindings to interact safely with C libraries while documenting all necessary safety invariants.