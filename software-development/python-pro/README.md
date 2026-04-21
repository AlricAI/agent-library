## Overview
Python Pro Developer is an advanced AI agent designed to function as a senior software engineer specializing in modern Python development practices. It masters the capabilities of Python 3.12 and beyond, ensuring all generated code adheres to contemporary standards for performance, type safety, and maintainability.

This agent integrates best-in-class tooling—such as `uv` for lightning-fast dependency management, `ruff` for comprehensive linting/formatting, and Pydantic for robust data validation—into every development cycle.

## Capabilities
*   **Modern Python Mastery:** Expert implementation of advanced features including structural pattern matching, context managers, and complex type hinting (Protocols).
*   **Asynchronous Programming:** Proficient in designing high-concurrency applications using `asyncio`, `aiohttp`, and modern async patterns.
*   **Tooling Integration:** Seamlessly utilizes the modern Python stack: managing dependencies with `uv` via `pyproject.toml`, enforcing quality with `ruff`, and structuring data models with Pydantic.
*   **Testing & Quality:** Builds comprehensive test suites using `pytest`, incorporating property-based testing (Hypothesis) and performance benchmarking.
*   **Architecture:** Capable of scaffolding full-stack components, particularly those involving FastAPI for API development.

## Example Use Cases
1. **Building a Microservice API:** Request the agent to scaffold a RESTful API using FastAPI, ensuring all request/response bodies are validated with Pydantic models and that the entire project structure is initialized correctly with `uv`.
2. **Performance Refactoring:** Provide an existing synchronous block of code and ask the agent to refactor it into an asynchronous pattern, optimizing resource handling using modern Python constructs.
3. **Code Quality Audit:** Submit a module and ask the agent to run a simulated audit, identifying potential linting issues (as if running `ruff`) or suggesting improvements for type hinting compliance.