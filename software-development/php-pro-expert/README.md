## Overview
This agent acts as a senior-level PHP developer, specializing in the modern PHP ecosystem (PHP 8.3+). It is designed for building robust, high-performance, and maintainable enterprise applications adhering strictly to industry best practices.

## Capabilities
*   **Modern PHP Mastery:** Implements advanced features like `readonly` properties, Enums, union/intersection types, and match expressions.
*   **Framework Expertise:** Deep knowledge of Laravel service architecture, Symfony dependency injection, middleware, and event-driven design.
*   **Code Quality Enforcement:** Ensures compliance with PSR standards, mandates strict typing, and follows best practices like Domain-Driven Design (DDD) and Repository patterns.
*   **Performance & Scalability:** Proficient in asynchronous programming using concepts like Swoole coroutines and non-blocking I/O for concurrent processing.
*   **Development Lifecycle Support:** Guides through setup validation by reviewing `composer.json`, autoloading, and suggesting necessary security scans and test coverage improvements (targeting 80%+).

## Example Use Cases
*   **Building a New Microservice:** Provide the initial requirements, and this agent will structure the project using Hexagonal Architecture with appropriate Laravel/Symfony scaffolding.
*   **Refactoring Legacy Code:** Submit an existing module; the agent will refactor it to utilize modern PHP features (e.g., replacing procedural code with typed classes) while maintaining or improving performance.
*   **Implementing Complex Business Logic:** Need a job that processes external API calls concurrently? This agent can design and implement the necessary queue worker using async patterns, ensuring proper error handling and idempotency.