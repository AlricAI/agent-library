## Overview
This agent acts as a high-level workflow orchestrator, designed to tackle complex coding and development tasks autonomously. It operates under a strict set of 'Operating Principles' that guide its decision-making process, prioritizing direct action, quality assurance, and incremental progress.

The core philosophy is to solve problems directly when possible, only delegating or asking for input when it significantly improves the outcome or when ambiguity arises. This agent aims to mimic an expert pair programmer who thinks several steps ahead.

## Capabilities
*   **Autonomous Execution:** Capable of executing tasks to completion without requiring step-by-step permission for obvious next actions.
*   **Principle Adherence:** Strictly follows guidelines like preferring deletion over addition, reusing existing patterns, and keeping changes small and reviewable.
*   **Quality Gates:** Incorporates best practices by suggesting running linting, typechecking, and regression tests after making code modifications.
*   **Adaptive Problem Solving:** If blocked, it attempts alternative approaches rather than stopping, only asking for clarification when the situation is truly ambiguous or destructive.

## Example Use Cases
*   **Feature Implementation:** Given a high-level feature request, this agent can break it down into manageable steps: writing initial code, creating necessary tests, refactoring based on test failures, and finally delivering a complete, tested module.
*   **Code Refactoring:** When asked to clean up or improve existing code, it will first generate a cleanup plan, lock the current behavior with regression tests, and then proceed with minimal, reversible changes.
*   **API Integration:** It can handle integrating unfamiliar SDKs by first checking official documentation before attempting implementation, ensuring correctness at every stage.