# AGENTS

> > See [root AGENTS.md](.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AGENTS.md - Backend

> See [root AGENTS.md](../AGENTS.md) for project-wide commands and guidelines.

## Overview

FastAPI backend with GraphQL API, Neo4j database, and async-first architecture.

## File Structure

- `infrahub/` – Main application
  - `api/` – REST endpoints
  - `graphql/` – GraphQL schema, mutations, resolvers
  - `core/` – Domain logic (nodes, schemas, branches, diff)
  - `database/` – Database utilities
  - `workers/` – Background tasks
- `tests/` – Test suites (unit, integration, functional, benchmark)
- `templates/` – Jinja2 code generation templates

## Commands

```bash
uv run invoke backend.test-unit        # Unit tests
uv run invoke backend.test-integration # Integration tests (needs Neo4j)
uv run invoke backend.format           # Format with ruff
uv run invoke backend.lint             # Lint with ruff + mypy
uv run invoke backend.generate         # Regenerate schemas/protocols
```

## Coding Standards

See `dev/guidelines/backend/python.md` for detailed coding standards including:

- Async-first patterns
- Pydantic models
- Docstring conventions
- Naming conventions
- Query patterns
- Type hints

### Neo4j/Cypher Queries

When writing or modifying Cypher queries, **read `dev/knowledge/backend/database-schema.md`** first. It documents:

- Vertex types (Root, Branch, Node, Relationship, Attribute, AttributeValue)
- Edge types and properties (branch, from, to, status)
- Temporal branching rules and valid path patterns
- Example queries for common operations

Also see `dev/knowledge/backend/query-pattern.md` for the Query class pattern used to execute Cypher queries.

## Testing

See `dev/knowledge/backend/testing.md` for detailed testing infrastructure documentation.

## Boundaries

### Always Do

- Use async/await for all I/O
- Type hint all function parameters and returns
- Use Pydantic models for data structures
- Use Query class pattern for database operations

### Ask First

- New database indexes
- Core schema definition changes
- New 

*[truncated — see source for full prompt]*