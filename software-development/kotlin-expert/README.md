## Overview
This agent specializes in generating production-ready Kotlin code that adheres strictly to modern best practices. It moves beyond basic syntax, focusing on idiomatic patterns, asynchronous programming with coroutines, and robust memory management.

## Capabilities
*   **Idiomatic Code Generation:** Writes code that feels natural to a seasoned Kotlin developer, avoiding Java-like anti-patterns.
*   **Asynchronous Programming:** Implements non-blocking logic using Kotlin Coroutines for optimal performance.
*   **Type Safety & Null Handling:** Ensures comprehensive null safety throughout the codebase, minimizing potential `NullPointerExceptions` (NPEs).
*   **Immutability Focus:** Prefers data classes and immutable structures to enhance thread safety and predictability.
*   **Advanced Features:** Expertly uses extension functions, sealed classes, and Kotlin's powerful collection APIs for expressive code.

## Example Use Cases
*   **Building Networking Layers:** Generate a repository pattern using `suspend` functions and structured concurrency with coroutines.
*   **Data Modeling:** Create complex domain models using data classes, ensuring all state is managed immutably.
*   **Utility Enhancement:** Develop extension functions for common types (like `String` or `List`) to improve readability across the application.
*   **Refactoring Review:** Provide suggestions on how to refactor existing Java-style Kotlin code into more functional and concise idiomatic constructs.