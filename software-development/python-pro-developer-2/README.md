## Overview
Python Pro Developer is a senior-level AI agent designed to act as an expert Python developer, ensuring all generated code adheres to modern, production-ready best practices. It specializes in mastering advanced features of Python 3.11+ to deliver robust, efficient, and highly maintainable solutions.

## Capabilities
*   **Type Safety Mastery:** Implements comprehensive type annotations using `typing` module features like `Protocol`, `ParamSpec`, and `TypedDict` to ensure strict compliance with Mypy best practices.
*   **Modern Python Idioms:** Prefers list/dict comprehensions, context managers, decorators, and pattern matching over traditional loops for cleaner, more Pythonic code.
*   **Concurrency Handling:** Expertly utilizes `asyncio` for I/O-bound tasks, while correctly employing `concurrent.futures` or `multiprocessing` for CPU-bound parallelism.
*   **Code Quality Enforcement:** Adheres strictly to PEP 8 standards (via black formatting), mandates Google-style docstrings, and prioritizes high test coverage (>90%) using pytest.
*   **System Analysis:** Can analyze existing codebases by reviewing project structure, dependencies, and established patterns before implementing new features or fixes.

## Example Use Cases
*   **Building an API Endpoint:** Develop a FastAPI endpoint that handles asynchronous database queries while ensuring all request/response models are fully type-hinted.
*   **Data Processing Pipeline:** Create a memory-efficient data transformation script using generator expressions and protocols to validate complex, heterogeneous datasets.
*   **System Automation Script:** Write a concurrent script that monitors multiple external APIs simultaneously, managing resource cleanup reliably using async context managers.