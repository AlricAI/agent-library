# CODE INDEXING API

> Complete reference for all Code Indexing MCP tools.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Code Indexing API Reference

Complete reference for all Code Indexing MCP tools. Each tool includes input parameters, return format, and usage examples.

## Table of Contents

- [Indexing Tools](#indexing-tools)
  - [code_index_project](#code_index_project)
  - [code_index_status](#code_index_status)
  - [code_list_projects](#code_list_projects)
  - [code_delete_project](#code_delete_project)
  - [code_reindex_file](#code_reindex_file)
- [Navigation Tools](#navigation-tools)
  - [code_get_project_stats](#code_get_project_stats)
  - [code_get_file_symbols](#code_get_file_symbols)
  - [code_get_symbols_overview](#code_get_symbols_overview)
- [Search Tools](#search-tools)
  - [code_find_symbol](#code_find_symbol)
  - [code_search_symbols_semantic](#code_search_symbols_semantic)
  - [code_search_pattern](#code_search_pattern)
  - [code_find_references](#code_find_references)
  - [code_hybrid_search](#code_hybrid_search)
- [Manipulation Tools](#manipulation-tools)
  - [code_replace_symbol](#code_replace_symbol)
  - [code_insert_after_symbol](#code_insert_after_symbol)
  - [code_insert_before_symbol](#code_insert_before_symbol)
  - [code_delete_symbol](#code_delete_symbol)

---

## Indexing Tools

### code_index_project

Start indexing a code project for semantic search capabilities.

**Description**: Scans the specified directory for source code files, parses them using tree-sitter to extract symbols (classes, functions, methods, etc.), generates embeddings for semantic search, and stores everything in the database. The indexing runs asynchronously in the background.

**Input Parameters**:

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `project_path` | string | ✅ | Absolute path to the project directory to index |
| `project_name` | string | ❌ | Human-readable name for the project. If omitted, uses the directory name |
| `languages` | string[] | ❌ | List of programming languages to index. If omitted, indexes all supported

*[truncated — see source for full prompt]*