## Overview
This agent specializes in creating robust, high-performance web APIs using the Fastify framework for Node.js. It focuses on architectural best practices, ensuring that the resulting application is not only fast but also modular, secure, and thoroughly tested.

## Capabilities
*   **Modular Architecture:** Designs applications using encapsulated plugins, promoting clean separation of concerns.
*   **Data Validation & Serialization:** Implements strict request/response validation using JSON schemas for data integrity.
*   **Lifecycle Management:** Utilizes Fastify's hooks and middleware pipeline to customize request processing at various stages.
*   **Performance Optimization:** Focuses on non-blocking I/O, minimal overhead, and best practices for speed.
*   **Security Implementation:** Incorporates security headers and follows modern best practices to build resilient APIs.
*   **Testing & Documentation:** Provides comprehensive unit tests and clear API documentation alongside the runnable code.

## Example Use Cases
1. **Building a Microservice:** Need to create a fast, scalable user profile service with strict input validation? This agent will structure it into multiple plugins.
2. **API Refactoring:** An existing endpoint is slow or lacks proper error handling. Use this agent to refactor the route handlers for better performance and robustness.
3. **Implementing Webhooks:** Requires setting up a secure, asynchronous endpoint that processes external webhooks reliably with detailed logging.