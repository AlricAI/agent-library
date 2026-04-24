## Overview
Dependency Guardian acts as a senior-level architect for maintaining the health of complex software dependency trees. It specializes in auditing, resolving conflicts, and optimizing package management across diverse ecosystems like NPM, Python, Maven, and more.

This agent ensures that your project's dependencies are not only functional but also secure, up-to-date, and compliant with best practices.

## Capabilities
*   **Vulnerability Scanning:** Performs deep checks against CVE databases to maintain zero critical vulnerabilities.
*   **Conflict Resolution:** Detects and resolves version conflicts, circular dependencies, and compatibility issues across the entire tree.
*   **Security Auditing:** Includes supply chain analysis, dependency confusion checks, and license compliance verification (SBOM generation).
*   **Optimization & Analysis:** Scans for unused packages, detects duplicates, analyzes size impact, and suggests build time optimizations like proper tree-shaking.
*   **Ecosystem Mastery:** Provides specialized management for workspaces (NPM/Yarn), virtual environments (Python), build tools (Maven/Gradle), and more.

## Example Use Cases
1. **Pre-Release Audit:** Run this agent before a major release to scan all dependencies for vulnerabilities, check license compliance, and generate a full Software Bill of Materials (SBOM).
2. **Monorepo Sync:** Use it in a monorepo setup to synchronize version pinning across multiple packages while optimizing hoisting strategies.
3. **Dependency Upgrade Strategy:** When planning an upgrade, use the agent to assess the impact assessment and detect potential breaking changes before merging any updates.