# CrewAI Development Rules

> CrewAI Development Rules Comprehensive best practices for developing with the CrewAI library, covering code organization, performance, security, testing, and common patterns. Based on actual CrewAI codebase analysis for accuracy. # General Best Practices:

## Tags
`python` `sqlite` `docker` `openai`

## System Prompt
# CrewAI Development Rules
# Comprehensive best practices for developing with the CrewAI library, covering code organization, performance, security, testing, and common patterns. Based on actual CrewAI codebase analysis for accuracy.

## General Best Practices:
- Leverage structured responses from LLM calls using Pydantic BaseModel for output validation.
- Use the @CrewBase decorator pattern with @agent, @task, and @crew decorators for proper organization.
- Regularly validate outputs from agents and tasks using built-in guardrails or custom validation.
- Use UV for dependency management (CrewAI's standard) with pyproject.toml configuration.
- Python version requirements: 3.10 to 3.14 (as per CrewAI's pyproject.toml).
- Prefer declarative YAML configuration for agents and tasks over hardcoded definitions.

## Code Organization and Structure:
- **Standard CrewAI Project Structure** (from CLI templates):
  - `project_name/` (Root directory)
    - `.env` (Environment variables - never commit API keys)
    - `pyproject.toml` (UV-based dependency management)
    - `knowledge/` (Knowledge base files)
    - `src/project_name/`
      - `__init__.py`
      - `main.py` (Entry point)
      - `crew.py` (Crew orchestration with @CrewBase decorator)
      - `config/`
        - `agents.yaml` (Agent definitions)
        - `tasks.yaml` (Task definitions)
      - `tools/`
        - `custom_tool.py` (Custom agent tools)
        - `__init__.py`
- **File Naming Conventions**:
  - Use descriptive, lowercase names with underscores (e.g., `research_agent.py`).
  - Pydantic models: singular names (e.g., `article_summary.py` with class `ArticleSummary`).
  - Tests: mirror source file name with `_test` suffix (e.g., `crew_test.py`).
- **CrewAI Class Architecture**:
  - Use @CrewBase decorator for main crew class.
  - Define agents with @agent decorator returning Agent instances.
  - Define tasks with @task decorator returning Task instances.
  - Define crew orchestration with @crew decorator 

*[truncated — see source for full prompt]*