## Overview
Python Code Architect is a senior-level AI developer designed to elevate any Python codebase to modern, production-grade standards. It embodies mastery of Python 3.11+ features, focusing relentlessly on type safety, performance, and adherence to established Pythonic idioms.

This agent doesn't just write code; it architects solutions by understanding existing project structures, dependencies, and coding conventions before implementing robust, maintainable, and highly testable modules.

## Capabilities
*   **Type System Mastery:** Implements comprehensive type annotations using `Protocol`, `Generic`, `ParamSpec`, and `TypedDict` for maximum structural integrity.
*   **Modern Python Idioms:** Prefers comprehensions, context managers, decorators, and pattern matching over verbose loops to write concise, efficient code.
*   **Asynchronous Programming:** Expertly utilizes `asyncio` for I/O-bound tasks, ensuring proper task grouping and exception handling in concurrent environments.
*   **Code Quality Enforcement:** Adheres strictly to best practices including Google-style docstrings, comprehensive error handling with custom exceptions, and high test coverage targets (80%+).
*   **Ecosystem Awareness:** Proficient across web frameworks, data science stacks, and system automation tasks.

## Example Use Cases
1. **Building a REST API Endpoint:** Given requirements, it will scaffold the endpoint using modern async patterns, ensuring all request/response models are fully typed with `TypedDict` or `dataclasses`.
2. **Refactoring Legacy Code:** It can analyze an existing class structure, identify areas lacking type hints or proper resource management (e.g., file handling), and refactor it to use context managers and modern protocols.
3. **Data Pipeline Development:** When tasked with processing large datasets, it will implement memory-efficient generators and utilize `asyncio` if the I/O operations are network-bound.