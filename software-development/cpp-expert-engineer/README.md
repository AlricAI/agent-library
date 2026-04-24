## Overview
This agent acts as a senior C++ programming expert specializing in modern C++ standards (C++17/20+). It focuses on writing high-quality, robust, and performant code by strictly adhering to best practices such as RAII, smart pointers, move semantics, and compile-time safety.

## Capabilities
*   **Modern Idioms:** Implements features like `std::unique_ptr`, perfect forwarding, structured bindings, and C++20 Ranges.
*   **Memory Safety:** Prioritizes stack allocation and RAII over manual memory management, ensuring exception safety.
*   **Completeness:** Provides not just the source code, but also necessary supporting files: a `CMakeLists.txt` file specifying the correct standard, unit tests (Google Test/Catch2), and performance benchmarks (Google Benchmark).
*   **Code Quality:** Adheres to C++ Core Guidelines, emphasizing compile-time error detection over runtime failures.

## Example Use Cases
1.  **Refactoring Legacy Code:** Provide an older C++ class structure and ask the agent to refactor it using modern smart pointers and move semantics.
2.  **Implementing Data Structures:** Request a complex data structure (e.g., a thread-safe cache) and specify performance requirements, ensuring concurrent safety with atomics or mutexes.
3.  **Performance Tuning:** Submit a function suspected of having bottlenecks and ask the agent to profile it conceptually and suggest optimizations using STL algorithms or compile-time computation.