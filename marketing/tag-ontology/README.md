# Tag Ontology

> This document provides comprehensive information about Genonaut's tag ontology system, which organizes content tags into a hierarchical structure for 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Tag Ontology Documentation

This document provides comprehensive information about Genonaut's tag ontology system, which organizes content tags into a hierarchical structure for improved search, discovery, and content organization.

## Overview

The tag ontology creates semantic relationships between tags used throughout the Genonaut system. Tags are organized in a monohierarchy using `rdfs:subClassOf` relationships, enabling:

- **Hierarchical browsing** - Navigate content through tag categories
- **Semantic search** - Find content using parent/child tag relationships
- **Enhanced recommendations** - Suggest content based on tag hierarchy
- **SPARQL queries** - Query the ontology using semantic web standards
- **Automatic tag suggestions** - Propose related tags during content creation

## Architecture

### Data Flow

```
Database (tags) → query_tags.py → Analysis → generate_hierarchy.py → TSV → JSON → Frontend
                                     ↓                                    ↓
                              Makefile Goals ← Manual Curation          API Server
```

### File Structure

```
genonaut/ontologies/tags/
├── scripts/           # Automation scripts
│   ├── generate_json.py      # TSV to JSON conversion
│   └── query_tags.py         # Database extraction
├── data/             # Generated data files
│   ├── hierarchy.tsv         # Source hierarchy data
│   └── hierarchy.json        # Frontend-ready JSON
├── queries/          # Example SPARQL queries
└── README.md         # Implementation documentation
```

### Database Integration

Tags are stored as JSON arrays in:
- `ContentItem.tags` - Manual content tags
- `ContentItemAuto.tags` - Automatically generated content tags

## Usage

### Basic Operations

```bash
# Extract latest tags from database
make ontology-refresh

# Generate hierarchy from analysis
make ontology-generate

# Validate hierarchy consistency
make ontology-validate

# Show ontology statistics
make ontology-stats
```

### Manual Cura

*[truncated — see source for full prompt]*