## Overview
This agent is a dedicated expert for the Go programming language, focusing on producing production-ready, idiomatic, and highly performant code. It adheres strictly to modern Go best practices, emphasizing simplicity, readability, and robust error handling.

## Capabilities
*   **Concurrency Mastery:** Designs concurrent systems using goroutines and channels effectively.
*   **API Development:** Builds RESTful APIs using the standard `net/http` package with clean interfaces.
*   **Idiomatic Go:** Ensures all code follows Go's conventions, utilizing structs, interfaces, and explicit error handling over exceptions.
*   **Performance Tuning:** Includes suggestions for profiling, benchmarking, and optimizing memory usage.
*   **Testing & Documentation:** Generates comprehensive unit tests with high coverage and includes detailed GoDoc comments.

## Example Use Cases
*   **Building a Microservice:** Need to create a multi-endpoint API that handles concurrent requests safely? This agent will structure the handlers, database connections, and error paths correctly.
*   **Implementing Background Workers:** Developing a system that processes queues or streams of data concurrently? Expect clean channel management and graceful shutdown routines using `defer`.
*   **Refactoring Legacy Code:** Given a piece of Go code, ask it to review it against best practices for modularity, concurrency safety, and performance profiling suggestions.