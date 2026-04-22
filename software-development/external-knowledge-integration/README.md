# External Knowledge Integration

> Complete implementation of external knowledge integration for the Neo4j memory system, allowing the framework to fetch, cache, and link external documentation sources to code and memories.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# External Knowledge Integration

Complete implementation of external knowledge integration for the Neo4j memory system, allowing the framework to fetch, cache, and link external documentation sources to code and memories.

## Overview

The External Knowledge Integration system provides:

- **Fetching & Caching**: Retrieve external documentation with HTTP caching and TTL
- **Graph Storage**: Store documentation in Neo4j with relationships to code and memories
- **Version Tracking**: Support multiple versions (Python 3.10 vs 3.12 docs)
- **Credibility Scoring**: Trust scores for different sources
- **Query & Retrieval**: Search and retrieve relevant documentation

## Architecture

### Core Components

```
src/amplihack/memory/neo4j/
├── external_knowledge.py      # Main implementation
│   ├── KnowledgeSource         # Enum: PYTHON_DOCS, MS_LEARN, GITHUB, etc.
│   ├── ExternalDoc             # Document dataclass
│   ├── APIReference            # API reference dataclass
│   └── ExternalKnowledgeManager # Main manager class
└── __init__.py                 # Exports external knowledge components

scripts/
├── import_external_knowledge.py    # CLI tool for importing docs
├── test_external_knowledge.py      # Integration tests (requires Neo4j)
└── test_external_knowledge_unit.py # Unit tests (no Neo4j required)
```

### Graph Schema

```cypher
# Nodes
(:ExternalDoc {
    url: STRING (UNIQUE),
    title: STRING,
    content: TEXT,
    source: STRING,
    version: STRING,
    trust_score: FLOAT,
    metadata: JSON,
    fetched_at: DATETIME,
    ttl_hours: INT
})

(:APIReference {
    id: STRING (UNIQUE),
    name: STRING,
    signature: STRING,
    doc_url: STRING,
    description: TEXT,
    examples: JSON,
    source: STRING,
    version: STRING
})

# Relationships
(:ExternalDoc)-[:EXPLAINS]->(:CodeFile)
(:ExternalDoc)-[:DOCUMENTS]->(:Function)
(:Memory)-[:SOURCED_FROM]->(:ExternalDoc)
```

## Usage

### Python API

#### Basic Document Fetching

```python
from amplihack.mem

*[truncated — see source for full prompt]*