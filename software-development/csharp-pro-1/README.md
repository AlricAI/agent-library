## Overview
CSharp Pro is an expert AI agent specializing in modern, enterprise-grade C# development within the .NET ecosystem. It adheres strictly to industry best practices, including SOLID principles, comprehensive error handling, and performance optimization techniques.

This agent ensures that generated code is not only functional but also maintainable, testable, and scalable for real-world applications, from simple services to complex microservices architectures.

## Capabilities
*   **Modern C# Implementation:** Utilizes advanced language features like records, pattern matching, and nullable reference types for expressive code.
*   **Architectural Adherence:** Implements design patterns favoring composition over inheritance while strictly following SOLID principles.
*   **Asynchronous Programming:** Writes correct `async/await` patterns with proper exception handling to prevent deadlocks and ensure non-blocking I/O.
*   **Testing Suite Generation:** Provides comprehensive unit tests using industry standards like xUnit, NUnit, Moq, and FluentAssertions.
*   **Performance Focus:** Optimizes code for performance by suggesting the use of `Span<T>`, value types, and memory management best practices.
*   **Documentation & Standards:** Includes thorough XML documentation comments and suggests necessary configuration files (e.g., EditorConfig).

## Example Use Cases
1. **Refactoring Legacy Code:** Paste a chunk of older C# code and ask the agent to refactor it using modern features, improving readability and safety.
2. **Building API Endpoints:** Request an ASP.NET Core Web API endpoint that handles complex business logic, ensuring proper dependency injection and robust validation.
3. **Implementing Data Access Layers:** Ask for a repository pattern implementation using Entity Framework Core, complete with unit tests mocking the database context.
4. **Concurrency Problem Solving:** Describe a multi-threaded operation and ask the agent to implement it safely using TPL constructs like `SemaphoreSlim` or `TaskCompletionSource`.