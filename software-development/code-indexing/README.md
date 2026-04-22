# CODE INDEXING

> The Code Indexing System provides powerful semantic code search and navigation capabilities for AI agents.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Code Indexing System

The Code Indexing System provides powerful semantic code search and navigation capabilities for AI agents. It uses tree-sitter for accurate parsing across 14+ programming languages and vector embeddings for semantic similarity search.

## Table of Contents

- [Features](#features)
- [Quick Start](#quick-start)
- [How It Works](#how-it-works)
- [Supported Languages](#supported-languages)
- [MCP Tools Overview](#mcp-tools-overview)
- [Configuration](#configuration)
- [Performance Considerations](#performance-considerations)
- [Troubleshooting](#troubleshooting)

## Features

- **Multi-Language Support**: Parse and index 14+ programming languages using tree-sitter
- **Semantic Search**: Find code by meaning, not just text matching
- **Symbol Extraction**: Automatically extract classes, functions, methods, interfaces, and more
- **Hierarchical Structure**: Maintain parent-child relationships between symbols
- **Incremental Indexing**: Only re-index files that have changed
- **Chunk-Based Search**: Large symbols are chunked for better semantic coverage
- **Hybrid Search**: Combine semantic similarity with structural filters

## Quick Start

### 1. Index a Project

Use the `code_index_project` tool to start indexing:

```json
{
  "project_path": "/path/to/your/project",
  "project_name": "My Project",
  "languages": ["go", "typescript", "python"]
}
```

Indexing runs asynchronously. Check status with `code_index_status`.

### 2. Search for Code

**Semantic Search** - Find code by meaning:
```json
{
  "project_id": "my-project",
  "query": "user authentication and session management",
  "limit": 10
}
```

**Find Symbol** - Find by name or path:
```json
{
  "project_id": "my-project",
  "name_path_pattern": "UserService/authenticate",
  "include_body": true
}
```

### 3. Navigate Code

**Get File Overview**:
```json
{
  "project_id": "my-project",
  "relative_path": "src/services/user.go"
}
```

**Get Project Stats**:
```json
{
  "project_id": "my-pr

*[truncated — see source for full prompt]*