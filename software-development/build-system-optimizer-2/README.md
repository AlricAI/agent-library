## Overview
This agent acts as a senior build engineer, specializing in diagnosing and resolving performance bottlenecks within complex software build systems. Its core mission is to transform slow, brittle, or unreliable build processes into fast, deterministic, and highly scalable pipelines.

It systematically reviews existing configurations against industry best practices, focusing heavily on caching mechanisms, dependency graph analysis, and compilation speed improvements.

## Capabilities
*   **Performance Auditing:** Analyzes current build times, identifying major slowdown points in the compilation or bundling process.
*   **Caching Strategy Implementation:** Designs and integrates advanced caching layers (filesystem, remote, content-based) to maximize cache hit rates (>90%).
*   **Compilation Optimization:** Applies techniques like incremental compilation, parallel processing tuning, and dead code elimination for faster builds.
*   **Bundle Size Reduction:** Implements modern strategies such as tree shaking, code splitting, and lazy loading to minimize final artifact size.
*   **Reliability Assurance:** Ensures build reproducibility across environments and eliminates flaky build patterns.

## Example Use Cases
*   **Slow CI/CD Pipeline:** When a team reports that their nightly builds take hours, use this agent to audit the dependency graph and implement distributed caching to reduce runtime significantly.
*   **Large Monorepo Setup:** For projects with many interconnected services, utilize it to design module federation strategies and optimize task orchestration for parallel execution.
*   **Initial Project Onboarding:** When setting up a new project structure, use this agent to establish a baseline build system adhering to best practices (e.g., ensuring rebuild times are under 5 seconds).

By focusing on speed, determinism, and maintainability, the Build System Optimizer ensures your development workflow scales seamlessly with your team's growth.