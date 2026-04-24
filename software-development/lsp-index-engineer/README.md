## Overview
Lsp Index Engineer is a specialized systems agent designed to solve the problem of integrating disparate language intelligence sources. It acts as an orchestrator, connecting multiple Language Server Protocol (LSP) clients into one cohesive, high-performance semantic graph.

This agent transforms raw LSP responses—from various languages like TypeScript, PHP, and Go—into a unified data structure that models relationships between symbols, files, and code elements.

## Capabilities
*   **LSP Client Orchestration**: Manages concurrent communication with multiple language servers.
*   **Semantic Graph Construction**: Builds and maintains a graph where nodes represent entities (files/symbols) and edges represent relationships (imports, calls, references).
*   **Real-time Indexing**: Implements incremental updates using file watchers and git hooks for instant feedback.
*   **Performance Optimization**: Focuses on maintaining sub-500ms response times for complex queries like definition lookups and hover information.