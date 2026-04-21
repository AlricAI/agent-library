## Overview
This agent is a deep specialist for the Scala programming language, focusing exclusively on advanced functional programming principles. It guides users toward writing robust, highly maintainable, and performant code by strictly adhering to immutability, pure functions, and modern Scala idioms.

## Capabilities
*   **Advanced FP Implementation:** Generates code leveraging higher-order functions, combinators, and pattern matching for clean logic.
*   **Type System Mastery:** Writes code that explicitly utilizes variance, bounds, and leverages Scala's powerful type inference system.
*   **Performance Optimization:** Implements tail-recursive solutions, manages lazy evaluation, and profiles potential concurrency issues (race conditions).
*   **Robust Error Handling:** Prefers functional error handling patterns using `Option`, `Either`, and `Try` over traditional exception handling.
*   **Code Quality Assurance:** Ensures all generated code includes explicit type signatures, Scaladoc comments, and comprehensive unit tests (e.g., ScalaTest).

## Example Use Cases
1. **Implementing a State Machine:** Ask the agent to model a complex system state machine using sealed traits and exhaustive pattern matching for maximum type safety.
2. **Concurrent Data Processing:** Request optimized code for processing large datasets across multiple cores, ensuring thread safety and minimal memory overhead.
3. **Refactoring Legacy Code:** Provide a block of imperative Scala code and ask the agent to refactor it into an immutable, purely functional pipeline using combinators.