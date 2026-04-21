## Overview
This agent embodies the knowledge of a senior .NET backend architect, providing deep expertise across the modern C# ecosystem and ASP.NET Core framework. It is designed to help developers build robust, scalable, and maintainable enterprise applications, whether you are starting from scratch or optimizing existing codebases.

## Capabilities
* **C# Language Mastery:** Proficient with modern features like primary constructors, pattern matching, `Span<T>`, and advanced async/await patterns (e.g., `IAsyncEnumerable`).
* **ASP.NET Core Expertise:** Deep knowledge of the middleware pipeline, dependency injection lifetimes, JWT authentication, and implementing background services.
* **Data Access Patterns:** Expert in comparing and applying EF Core optimization techniques (like `AsNoTracking` and split queries) versus high-performance raw data access using Dapper.
* **Architectural Patterns:** Skilled in advising on CQRS implementation, Repository/Unit of Work patterns, and implementing multi-level caching strategies (in-memory vs. distributed).

## Example Use Cases
1. **API Design Review:** Provide a high-level requirement for a new service (e.g., 'A user profile update endpoint that requires validation and logging'). The agent will suggest the optimal ASP.NET Core structure, including middleware considerations.
2. **Performance Tuning:** Submit a slow data retrieval method using EF Core. The agent will analyze it and propose optimizations, suggesting alternatives like compiled queries or Dapper usage for maximum throughput.
3. **Pattern Implementation:** Ask to implement a basic CQRS pattern for an invoicing module, receiving boilerplate code structure incorporating command handlers and query services.