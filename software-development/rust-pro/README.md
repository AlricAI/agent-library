## Overview
Rust Pro is an expert AI agent designed to assist developers working with modern Rust (1.75+). It specializes in building high-performance, memory-safe systems and mastering complex asynchronous patterns required for production-grade applications.

This agent goes beyond basic syntax help, focusing on advanced concepts like generic associated types, sophisticated concurrency management using Tokio, and deep understanding of Rust's ownership model to ensure optimal code quality and speed.

## Capabilities
*   **Modern Language Features:** Expertise in Rust 1.75+ features, including const generics, advanced pattern matching, and procedural macros.
*   **Concurrency & Async:** Mastery of `async/await` with the Tokio runtime, stream processing, backpressure handling, and complex channel patterns (mpsc, broadcast).
*   **Memory Safety:** Deep knowledge of ownership rules, smart pointers (`Arc`, `Mutex`), RAII patterns, and zero-cost abstractions for performance optimization.
*   **Web Frameworks:** Proficient in building services using modern frameworks like Axum and Tower.
*   **Type System Mastery:** Ability to handle advanced trait bounds, associated types, and type-level programming concepts.

## Example Use Cases
*   **Building a High-Throughput API:** Ask it to scaffold an entire RESTful service using `axum` that handles concurrent requests efficiently.
*   **Performance Bottleneck Identification:** Provide existing code and ask it to refactor sections for better memory layout or async efficiency, suggesting improvements with Tokio primitives.
*   **Implementing Complex State Management:** Use it to design a system requiring shared, mutable state across multiple asynchronous tasks, ensuring correct use of `Arc<Mutex<T>>`.
*   **Learning Advanced Concepts:** Request detailed explanations and working examples for concepts like Generic Associated Types (GATs) or advanced lifetime annotations.