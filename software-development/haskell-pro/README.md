## Overview
Haskell Pro is an advanced AI agent designed to act as a senior Haskell architect and expert programmer. It specializes in building robust, high-assurance software using the principles of pure functional programming.

This agent focuses on leveraging Haskell's powerful type system—including GADTs, type families, and newtypes—to model domain logic with mathematical rigor, ensuring that code is not only correct but also provably safe where possible.

## Capabilities
*   **Advanced Type Modeling:** Generates code utilizing advanced features like GADTs, phantom types, and precise invariants to eliminate runtime errors at compile time.
*   **Pure Architecture Design:** Structures applications by isolating all `IO` effects to explicit boundaries, maximizing the use of pure functions for testability and reasoning.
*   **Concurrency Management:** Provides idiomatic solutions for concurrent programming using Software Transactional Memory (STM) and `async`, ensuring exception safety.
*   **Parsing & Serialization:** Generates robust parsing logic using Megaparsec and handles JSON serialization/deserialization with Aeson, always emphasizing type safety.
*   **Testing & Verification:** Includes suggestions for property-based testing using QuickCheck or unit tests using Hspec to validate invariants automatically.

## Example Use Cases
1. **Designing a State Machine:** Ask it to model a complex workflow (e.g., an order lifecycle) using GADTs, ensuring that illegal state transitions are impossible to compile.
2. **Implementing a Parser:** Provide a grammar definition and request the full parsing pipeline using Megaparsec, including error reporting.
3. **Concurrency Pattern:** Ask for a worker pool implementation pattern using STM to manage shared, mutable resources safely across multiple threads.
4. **Refactoring Advice:** Submit existing imperative or poorly typed Haskell code and ask it to refactor it into a more purely functional, idiomatic structure with clear type signatures.