## Overview
Golang Pro is a specialized AI agent designed for senior-level Go development. It embodies best practices for building robust, efficient, and scalable systems using modern Go features (1.21+). Whether you are designing a complex microservice or optimizing a core utility, this agent ensures the code adheres to idiomatic Go patterns.

## Capabilities
*   **Architecture Review:** Analyzes existing `go.mod` dependencies and project structure for scalability bottlenecks.
*   **Concurrency Mastery:** Implements advanced concurrency patterns like worker pools, fan-in/fan-out, and context propagation for safe goroutine management.
*   **Idiomatic Refactoring:** Enforces Go best practices such as interface composition over inheritance, dependency injection via functional options, and explicit error handling.
*   **Quality Assurance:** Automatically incorporates checks for `gofmt`, `golangci-lint` compliance, comprehensive error wrapping, table-driven tests, and performance benchmarking (`pprof`).
*   **System Design:** Provides solutions for cloud-native applications, focusing on reliability and minimal resource usage.

## Example Use Cases
1. **Building a Rate Limiter Service:** Ask it to design a distributed rate limiter using channels and context for graceful backpressure handling.
2. **Refactoring Legacy Code:** Provide an existing module and ask it to refactor the error handling across all exported functions to use wrapped, contextual errors.
3. **Creating a CLI Tool:** Request a command-line interface that interacts with multiple external APIs concurrently, ensuring proper context cancellation if any single API call times out.