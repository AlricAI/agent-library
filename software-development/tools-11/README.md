# TOOLS

> This file defines all tools and shared resources available to the software development team agents.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Software Development Team Tools Configuration

This file defines all tools and shared resources available to the software development team agents. Each tool is defined as a variable that agents can reference in their contexts.

## Version Control
- **VERSION_CONTROL**: Git
  - Command: `git`
  - Conventions: See CONVENTIONS.md for branch patterns and commit standards
  - Remote: As configured in project `.git/config`

## Project Management
- **PROJECT_MANAGEMENT_TOOL**: [To be configured based on organization preference]
  - Examples: Jira, GitHub Issues, Linear, Asana
  - Access: Via API or CLI as configured
  - Updates: Daily progress, sprint status, blockers

## Development Tools
- **BUILD_SYSTEM**: [Language-specific, passed as argument]
  - JavaScript/TypeScript: `npm`, `yarn`, or `pnpm`
  - Python: `pip`, `poetry`, or `pipenv`
  - Java: `maven` or `gradle`
  - Go: `go build`
  - Rust: `cargo`

## Testing Tools
- **TEST_RUNNER**: [Language-specific, determined by project]
  - JavaScript/TypeScript: `jest`, `mocha`, `vitest`
  - Python: `pytest`, `unittest`
  - Java: `junit`
  - Go: `go test`
  - Rust: `cargo test`

## Code Quality Tools
- **LINTER**: [Language-specific]
  - JavaScript/TypeScript: `eslint`, `prettier`
  - Python: `ruff`, `black`, `flake8`
  - Java: `checkstyle`, `spotbugs`
  - Go: `golangci-lint`
  - Rust: `clippy`

- **COVERAGE_REPORTER**: [Language-specific]
  - JavaScript/TypeScript: `jest --coverage`, `nyc`
  - Python: `pytest-cov`, `coverage.py`
  - Java: `jacoco`
  - Go: `go test -cover`
  - Rust: `cargo tarpaulin`

## Shared Memory Systems
- **TEAM_MEMORY**: `./TEAM_MEMORY.md`
  - Purpose: Team-specific knowledge, decisions, patterns
  - Access: Read/write for all team members
  - Updates: After significant decisions or learnings

- **CROSS_TEAM_MEMORY**: `../CROSS_TEAM_MEMORY.md`
  - Purpose: Inter-team communication and coordination
  - Access: Read/write for authorized agents (Manager role)
  - Updates: When coordinating with other t

*[truncated — see source for full prompt]*