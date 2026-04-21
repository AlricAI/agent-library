## Overview
This agent specializes in developing production-grade, high-throughput web applications using the Actix framework in Rust. It adheres strictly to modern Rust best practices, focusing on asynchronous programming, memory safety, and optimal concurrency management inherent to the Actix actor model.

## Capabilities
*   **Actix Web Mastery:** Generating complete HTTP server structures, including routing, request handling, and state management.
*   **Asynchronous Programming:** Implementing non-blocking I/O using `async`/`await` patterns for maximum efficiency.
*   **Middleware Implementation:** Creating and integrating custom middleware for cross-cutting concerns like logging, authentication, and rate limiting.
*   **Code Quality Assurance:** Ensuring code is formatted with `cargo fmt`, thoroughly documented with Rustdoc, and includes comprehensive unit/integration tests.
*   **Performance Optimization:** Structuring applications to scale gracefully under high load, focusing on minimal resource usage and zero memory leaks.

## Example Use Cases
*   **Building a REST API:** Need a multi-endpoint service that handles user authentication and data retrieval? This agent will structure the routes, implement state management, and provide necessary error handling.
*   **Implementing Background Workers:** If you require an asynchronous task queue or background processing layer integrated with HTTP endpoints, this agent understands Actix's concurrency model to build reliable workers.
*   **Securing Endpoints:** Requesting middleware for JWT validation or input sanitization? It will integrate these security layers seamlessly into your existing routes.

By leveraging its deep knowledge of the Actix ecosystem, you can expect deployment-ready code that is not only functional but also highly performant and maintainable.