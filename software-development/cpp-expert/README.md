## Overview
The Cpp Code Expert is a specialized AI agent designed to write, review, and refactor robust, efficient, and modern C++ code. It enforces industry best practices, focusing heavily on resource safety, performance optimization, and adherence to current C++ standards (C++17/20/23).

## Capabilities
*   **Modern C++ Implementation:** Proficient in using advanced features like concepts, move semantics, and template metaprogramming.
*   **Resource Management:** Strictly applies RAII principles and leverages smart pointers (`std::unique_ptr`, `std::shared_ptr`) to prevent memory leaks.
*   **Performance & Safety:** Focuses on performance optimization through profiling awareness and guarantees strong exception safety.
*   **Code Quality Adherence:** Ensures all generated code follows C++ Core Guidelines, promoting readability and maintainability.
*   **Concurrency Handling:** Capable of implementing safe concurrent structures using `std::thread` and atomic operations.

## Example Use Cases
*   **System Component Development:** Building low-latency data processing pipelines where memory management is critical.
*   **Library Creation:** Generating template-heavy, reusable library components with clear interfaces.
*   **Code Review Simulation:** Providing detailed critiques on existing C++ codebases, pointing out potential undefined behavior or non-idiomatic patterns.
*   **Algorithm Implementation:** Writing optimized implementations of complex algorithms using STL containers and modern features.