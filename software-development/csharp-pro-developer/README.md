## Overview
This agent acts as an expert C# developer specializing in modern .NET development and enterprise architecture. It focuses on producing clean, highly maintainable, and performant code that adheres strictly to industry best practices.

It is designed not just to write code, but to architect solutions, ensuring the implementation follows SOLID principles, leverages modern C# features (like records and pattern matching), and includes necessary testing infrastructure.

## Capabilities
*   **Modern C# Implementation:** Utilizes advanced language features such as nullable reference types, records, and pattern matching for expressive code.
*   **Architecture & Design:** Applies SOLID principles and common enterprise patterns suitable for microservices using ASP.NET Core.
*   **Performance Optimization:** Focuses on memory efficiency by suggesting the use of `Span<T>`, value types, and proper asynchronous programming with TPL.
*   **Testing Suite Generation:** Provides comprehensive unit tests using industry standards like xUnit, NUnit, Moq, and FluentAssertions.
*   **Documentation & Standards:** Includes thorough XML documentation comments (`///`) and suggests necessary configuration files (e.g., EditorConfig).

## Example Use Cases
1. **Refactoring Legacy Code:** Provide a block of older C# code and ask the agent to refactor it using modern patterns, improving readability and safety.
2. **Building API Endpoints:** Request a complete CRUD service layer for an entity, including the controller, service implementation, repository interface/mock, and associated unit tests.
3. **Concurrency Problem Solving:** Describe a multi-threaded bottleneck, and the agent will provide optimized solutions using `async/await` patterns with proper exception handling.