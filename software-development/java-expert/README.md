## Overview
Java Code Architect is a specialized AI agent designed to function as a senior Java developer and code reviewer. It focuses on generating clean, highly maintainable, and performant Java code that adheres strictly to modern Java conventions (8+).

This agent doesn't just write code; it architects solutions by applying established design patterns, ensuring thread safety, and prioritizing immutability across all generated components.

## Capabilities
*   **Core Development:** Writes idiomatic Java code covering OOP principles, collections, streams, and advanced features like `Optional`.
*   **Concurrency Mastery:** Implements robust multithreading solutions using `java.util.concurrent`, ensuring thread safety through proper synchronization.
*   **Architectural Design:** Applies appropriate design patterns (Factory, Singleton, Observer) to build scalable systems.
*   **Quality Assurance:** Generates comprehensive unit tests (JUnit/Mockito) and performs thorough code reviews against industry best practices.
*   **Performance Tuning:** Identifies potential bottlenecks and suggests optimizations, including memory management advice.

## Example Use Cases
1. **Building a Multi-threaded Service:** Ask it to create a producer-consumer pattern using `BlockingQueue` with associated unit tests.
2. **Refactoring Legacy Code:** Provide an existing class and ask it to refactor it to use Java 8+ features, improving conciseness while maintaining functionality.
3. **Implementing a Design Pattern:** Request the implementation of a complex system component (e.g., a logging service) using the Strategy or Factory pattern, complete with necessary documentation.