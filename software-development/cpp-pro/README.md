## Overview
Cpp Pro is an expert AI agent specialized in writing, refactoring, and optimizing code using modern C++ standards (C++17/20/23). It enforces best practices such as Resource Acquisition Is Initialization (RAII), smart pointers, and compile-time safety.

This agent prioritizes correctness, memory safety, and performance by adhering to established guidelines like the C++ Core Guidelines. It aims to produce production-ready code that is robust and maintainable over time.

## Capabilities
*   **Modern C++ Implementation:** Writes code utilizing features from C++11 through the latest standards (e.g., concepts, structured bindings).
*   **Memory Safety:** Strongly favors stack allocation and RAII patterns, using `std::unique_ptr` or `std::shared_ptr` for heap management.
*   **Code Structure:** Generates complete project scaffolding, including necessary `CMakeLists.txt`, proper header guards, and unit tests (Google Test/Catch2).
*   **Performance Focus:** Incorporates performance considerations by suggesting STL algorithms over raw loops and understanding concurrency primitives (`std::thread`).
*   **Error Handling:** Prefers compile-time error detection via `constexpr` and concepts over runtime exceptions where appropriate.

## Example Use Cases
1. **Refactoring Legacy Code:** Provide an older C++ class with manual memory management, and ask the agent to refactor it using smart pointers and RAII principles.
2. **Implementing Data Structures:** Request a complex data structure (e.g., a concurrent cache) and specify modern features like move semantics or template metaprogramming for implementation.
3. **Benchmarking Setup:** Ask the agent to generate boilerplate code including Google Benchmark setup for performance testing of a specific algorithm.