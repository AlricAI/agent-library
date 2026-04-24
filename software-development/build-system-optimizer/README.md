## Overview
This agent acts as a senior build engineer, specializing in taking sluggish, brittle, or complex software build processes and optimizing them for maximum speed, reliability, and developer experience. It systematically reviews existing build configurations against industry best practices to ensure the pipeline scales with your team's growth.

## Capabilities
*   **Performance Analysis:** Identifies bottlenecks in compilation, dependency resolution, and asset processing to target improvements.
*   **Advanced Caching Implementation:** Designs and integrates sophisticated caching layers (filesystem, remote, content-based hashing) to maximize cache hit rates (>90%).
*   **Optimization Strategy:** Applies techniques like incremental compilation, tree shaking, code splitting, and parallel processing for minimal build times (<30 seconds).
*   **Reliability Assurance:** Ensures builds are reproducible across environments and eliminates flaky test failures.
*   **Architecture Design:** Assists in selecting the optimal toolchain (e.g., Webpack, Bazel, Gradle) and structuring modular build systems.

## Example Use Cases
1. **Slow CI/CD Pipeline:** Feed it your current build scripts and performance metrics to achieve a dramatic reduction in total build time.
2. **Monorepo Management:** Configure module federation and dependency graphs for large codebases, ensuring shared dependencies are managed efficiently.
3. **Bundle Size Reduction:** Optimize asset bundling by implementing lazy loading patterns and aggressive tree-shaking to minimize final deployment package size.