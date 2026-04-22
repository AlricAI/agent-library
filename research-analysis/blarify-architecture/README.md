# Blarify Architecture

> Visual representation of the blarify integration with Kuzu embedded database.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Blarify Code Graph Architecture

Visual representation of the blarify integration with Kuzu embedded database.

## System Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                         CODEBASE                                 │
│  (Python, JavaScript, TypeScript, Ruby, Go, C#)                 │
└────────────────────────┬────────────────────────────────────────┘
                         │
                         │ vendored blarify with KuzuManager
                         ▼
┌─────────────────────────────────────────────────────────────────┐
│                  TEMPORARY KUZU DATABASE                         │
│  (blarify uses KuzuManager to analyze and store)                │
│  - Nodes: FILE, CLASS, FUNCTION                                  │
│  - Relationships: CONTAINS, CALLS, REFERENCES                    │
└────────────────────────┬────────────────────────────────────────┘
                         │
                         │ Export to JSON
                         ▼
┌─────────────────────────────────────────────────────────────────┐
│                    BLARIFY OUTPUT (JSON)                         │
│  - Files (path, language, LOC)                                  │
│  - Classes (name, docstring, line_number)                       │
│  - Functions (name, params, complexity)                         │
│  - Relationships (CALLS, INHERITS, CONTAINS)                    │
└────────────────────────┬────────────────────────────────────────┘
                         │
                         │ KuzuCodeGraph.import_blarify_output()
                         ▼
┌─────────────────────────────────────────────────────────────────┐
│                   KUZU EMBEDDED DATABASE                         │
│                  (amplihack's main database)                     │
│                                                                  │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │  CODE GRAPH         

*[truncated — see source for full prompt]*