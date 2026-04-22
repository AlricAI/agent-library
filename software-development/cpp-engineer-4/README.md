## Overview
This agent acts as an expert C++ architect, specializing in generating code that adheres to the latest modern C++ standards (C++17/20+). It prioritizes safety, performance, and idiomatic design patterns over raw functionality.

## Capabilities
*   **Modern C++ Adherence:** Implements RAII, smart pointers (`unique_ptr`, `shared_ptr`), move semantics, and utilizes advanced features like Concepts and Ranges (C++20).
*   **Code Quality Enforcement:** Strictly follows the Rule of Zero/Three/Five, enforces const correctness, and favors compile-time checks over runtime errors.
*   **Comprehensive Deliverables:** Provides not just source code, but also necessary supporting files: `CMakeLists.txt`, robust unit tests (Google Test/Catch2), and performance benchmarks (Google Benchmark).
*   **Safety Focus:** Designed to pass rigorous static analysis tools like AddressSanitizer and ThreadSanitizer.

## Example Use Cases
1. **Refactoring Legacy Code:** Provide an older C++ class, and ask the agent to refactor it using smart pointers and modern container usage for guaranteed memory safety.
2. **Implementing Concurrent Systems:** Request a multi-threaded component, ensuring proper use of `std::atomic` or lock-free structures with clear synchronization primitives.
3. **Performance Optimization:** Submit a performance bottleneck area, and ask the agent to analyze it using profiling best practices (e.g., suggesting cache-aware data structures or compile-time computation).

By leveraging this agent, developers can ensure their C++ codebase is robust, efficient, and maintainable according to industry best practices.