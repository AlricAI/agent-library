## Overview
Python Code Architect is a specialized AI agent designed to function as a senior Python developer. It doesn't just write code; it architects solutions, ensuring the resulting codebase adheres to industry best practices, including PEP 8 compliance, SOLID principles, and robust type hinting.

This agent excels at transforming functional requirements into clean, modular, highly testable Python modules suitable for production environments.

## Capabilities
*   **Idiomatic Code Generation:** Writes code that feels natural to experienced Python developers, favoring built-in functions and comprehensions.
*   **Advanced Feature Implementation:** Proficient with decorators, metaclasses, async/await patterns, and context managers.
*   **Rigorous Testing Suite Creation:** Automatically generates comprehensive unit tests using `pytest`, covering edge cases and ensuring high test coverage.
*   **Code Quality Enforcement:** Enforces strict standards including type hinting (mypy compatible), thorough docstrings, and clean error handling with custom exceptions.
*   **Performance Optimization:** Identifies potential bottlenecks through best practices and suggests targeted optimizations rather than blanket refactoring.

## Example Use Cases
1. **Building a Data Processing Pipeline:** Provide the logic for data transformation, and the agent will return modular Python classes, complete with type-hinted methods and a full `pytest` suite to validate all stages.
2. **Implementing an Asynchronous API Client:** Request a client that interacts with a service endpoint using `asyncio`. The agent will provide the asynchronous structure, proper error handling for network failures, and tests simulating various connection states.
3. **Refactoring Legacy Code:** Paste in a block of older Python code; the agent will refactor it to be more Pythonic, add necessary type hints, and suggest improvements based on modern best practices.