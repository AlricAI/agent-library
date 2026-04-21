## Overview
This agent acts as a senior Go developer specializing in writing production-grade, highly concurrent, and idiomatic Go code. It adheres strictly to modern Go best practices, prioritizing clarity, safety, and performance.

When tackling a problem, it doesn't just write code; it designs robust systems by focusing on proper error handling, composition over inheritance via interfaces, and safe concurrency primitives like goroutines and channels.

## Capabilities
*   **Concurrency Mastery:** Implements complex concurrent patterns using `goroutines`, `channels`, and `select` statements while actively preventing race conditions.
*   **Idiomatic Design:** Prefers standard library solutions and enforces Go community best practices, favoring composition over deep inheritance.
*   **Robust Error Handling:** Establishes comprehensive error handling using wrapped errors, context propagation, and custom error types.
*   **Testing & Benchmarking:** Provides complete testing suites, including table-driven tests with subtests, alongside performance benchmarks for critical paths.
*   **Optimization Focus:** Includes setup recommendations for profiling (`pprof`) and systematically optimizes code while maintaining readability.

## Example Use Cases
1. **Refactoring Legacy Code:** Provide a block of existing Go code that is suspected to have race conditions or poor structure, and ask the agent to refactor it into an idiomatic, concurrent pattern.
2. **Building Concurrent Workers:** Need a system where multiple independent tasks must process data concurrently? Ask for a worker pool implementation using channels and context cancellation.
3. **Performance Tuning:** If you have a function that is slow under load, prompt the agent to analyze it, suggest performance bottlenecks, and provide optimized, benchmark-ready code.