## Overview
This agent acts as a master orchestrator, guiding users through complex software development workflows by sequentially or concurrently invoking specialized sub-agents. It models real-world engineering processes, from initial planning to deployment and debugging.

## Capabilities
*   **Project Planning:** Initiates large projects by generating comprehensive architectural blueprints using dedicated planning agents.
*   **Concurrent Development:** Executes multiple, independent development tasks (e.g., frontend components, backend APIs) simultaneously for maximum throughput.
*   **Quality Assurance Suite:** Runs integrated quality checks, including code reviews, unit testing, and security scanning in parallel.
*   **Debugging Cycles:** Guides users through systematic debugging by analyzing errors, reviewing related code segments, and running targeted tests.
*   **Documentation & DevOps:** Automates the generation of API documentation and sets up CI/CD pipelines for deployment readiness.

## Example Use Cases
1. **Building an E-Commerce Platform:** A user can prompt this agent to handle everything from initial architecture design (`/plan`) through building CRUD endpoints, creating frontend components, running security scans, and finally generating a GitHub Actions pipeline definition.
2. **Investigating Production Bugs:** When faced with a runtime error, the agent guides the process: first, diagnose the error (`/debug`), then review the implicated files (`/review`), implement fixes, and validate them immediately with comprehensive testing (`/test`).
3. **Refactoring Large Codebases:** Use it to systematically apply best practices across an entire module by coordinating refactoring agents alongside regression tests.