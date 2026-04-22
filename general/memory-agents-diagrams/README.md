# MEMORY AGENTS DIAGRAMS

> This file is the presentation-friendly companion to `docs/concepts/memory-enabled-agents-architecture.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Memory Systems Diagrams

This file is the presentation-friendly companion to `docs/concepts/memory-enabled-agents-architecture.md`.

## Diagram 1: Two Memory Surfaces

```mermaid
flowchart LR
    CLI[amplihack memory tree / clean] --> RepoMemory[src/amplihack/memory]
    RepoMemory --> Kuzu[(~/.amplihack/memory_kuzu.db)]
    RepoMemory --> SQLite[(optional sqlite backend)]

    Generator[amplihack new --enable-memory] --> Package[generated goal-agent package]
    Package --> MainPy[main.py memory helpers]
    Package --> Config[memory_config.yaml]
    Package --> AgentMemory[(./memory/)]
    MainPy --> ExperienceStore[amplihack_memory ExperienceStore]
    ExperienceStore --> AgentMemory
```

### Speaker Notes

- The repo has one memory story for the top-level CLI and another for generated standalone agents.
- The CLI-facing backend is graph-oriented and Kuzu-first.
- Generated agents package an experience-store scaffold under their own `./memory/` directory.

## Diagram 2: In-Repo Memory Backend

```mermaid
flowchart TD
    Command[amplihack memory tree / clean] --> BackendChoice{backend}
    BackendChoice -->|default| KuzuBackend[Kuzu backend]
    BackendChoice -->|optional| SqliteBackend[SQLite backend]
    KuzuBackend --> Env1[AMPLIHACK_GRAPH_DB_PATH]
    KuzuBackend --> Env2[AMPLIHACK_KUZU_DB_PATH\nDeprecated alias]
    KuzuBackend --> DefaultPath[~/.amplihack/memory_kuzu.db]
    KuzuBackend --> Graph[graph memory + code linking]
```

### Speaker Notes

- `tree` and `clean` are the verified top-level memory commands in this checkout.
- Kuzu is the default backend.
- `AMPLIHACK_GRAPH_DB_PATH` is the preferred environment variable.

## Diagram 3: Memory Type Model

```mermaid
flowchart LR
    Primary[preferred memory types] --> Episodic[episodic]
    Primary --> Semantic[semantic]
    Primary --> Procedural[procedural]
    Primary --> Prospective[prospective]
    Primary --> Working[working]

    Legacy[legacy compatibility types] --> Conversation[conversation]


*[truncated — see source for full prompt]*