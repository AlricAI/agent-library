# TOOL HELP SYSTEM

> The `how_to_use` tool provides on-demand documentation for remembrances-mcp tools, significantly reducing initial context token consumption while maintaining full functionality.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Tool Help System (how_to_use)

The `how_to_use` tool provides on-demand documentation for remembrances-mcp tools, significantly reducing initial context token consumption while maintaining full functionality.

## Overview

Instead of loading detailed descriptions for all 37+ tools at startup (consuming ~15,000+ tokens), the system now provides:
- **Minimal descriptions** (1-2 lines) for each tool in the initial context
- **Full documentation** available on-demand via `how_to_use()`

This results in approximately **85% reduction** in initial token consumption.

## Usage

### Get Complete Overview
```
how_to_use()
```
Returns a high-level overview of all tool categories (memory, knowledge base, code indexing).

### Get Group Documentation
```
how_to_use("memory")     # Memory tools (facts, vectors, graph)
how_to_use("kb")         # Knowledge base tools
how_to_use("code")       # Code indexing and search tools
```

### Get Specific Tool Documentation
```
how_to_use("remembrance_save_fact")
how_to_use("kb_add_document")
how_to_use("index_repository")
how_to_use("search_code")
```

## Tool Categories

### Memory Tools (`memory`)
- **Fact Tools**: Key-value storage (`remembrance_save_fact`, `remembrance_get_fact`, etc.)
- **Vector Tools**: Semantic search (`remembrance_add_vector`, `remembrance_search_vectors`, etc.)
- **Graph Tools**: Entity/relationship management (`remembrance_create_entity`, `remembrance_traverse_graph`, etc.)

### Knowledge Base Tools (`kb`)
- Document storage and retrieval (`kb_add_document`, `kb_get_document`, etc.)
- Semantic document search (`kb_search_documents`)

### Code Tools (`code`)
- **Indexing**: Repository/file indexing (`index_repository`, `index_directory`, etc.)
- **Search**: Code and symbol search (`search_code`, `search_symbols`, etc.)
- **Analysis**: Code analysis tools (`get_file_summary`, `find_references`, etc.)

## Documentation Structure

The documentation is embedded in the binary using Go's `//go:embed` directive:

```
pkg

*[truncated — see source for full prompt]*