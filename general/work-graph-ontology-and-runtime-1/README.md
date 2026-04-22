# Work Graph Ontology And Runtime

> This document explains the **internal property-graph ontology** used by `work`,
how that graph is **materialized at runtime**, and what **“stateless”*

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Internal Graph Ontology and Runtime Model

This document explains the **internal property-graph ontology** used by `work`,
how that graph is **materialized at runtime**, and what **“stateless”** means in
practice for the CLI.

The goal is to make one thing explicit:

> `work` does **not** rebuild, mirror, or cache entire projects.
> It operates on **ephemeral graph slices** that exist only for the duration of a command.

---

## 1. The Core Graph Ontology

### 1.1 Ontology Overview

At its core, `work` models task management as a **property graph**:

- **Nodes** represent work items
- **Edges** represent explicit relationships
- **Properties** capture minimal, stable metadata

This ontology is deliberately small and stable.

**Standards Alignment**: `work` aligns its core concepts with [OSLC CM vocabulary](https://docs.oasis-open.org/oslc-domains/cm/v3.0/cm-v3.0.html) where possible, while deliberately exceeding it with a graph-based internal model that supports explicit relationships and cross-tool workflows.

---

### 1.2 Node: `WorkItem`

`WorkItem` is the only mandatory node type.

**Core properties:**

| Property | Type | Description |
|--------|------|-------------|
| `id` | string | Context-qualified, opaque identifier |
| `kind` | string | task, epic, bug, etc. |
| `state` | enum | `new`, `active`, `closed` |
| `title` | string | Human-readable title |
| `description` | string | Optional text |
| `assignee` | string | `unassigned` allowed |
| `priority` | enum | `low`, `medium`, `high` |
| `createdAt` | timestamp | Creation time |
| `updatedAt` | timestamp | Last modification |

Extensions and tool-specific data are namespaced and optional.

---

### 1.3 Edge Types (Relations)

Edges are **typed and explicit**.

| Relation | Directed | Meaning |
|--------|----------|--------|
| `child_of` | yes | Hierarchy |
| `parent_of` | yes | Inverse hierarchy |
| `precedes` | yes | Temporal dependency |
| `succeeds` | yes | Inverse |
| `blocks` | yes | Blocking depend

*[truncated — see source for full prompt]*