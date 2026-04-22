# Work Local Fs Execution Flow

> This document describes **how a single user command is executed internally**
when using the `local-fs` adapter, with a focus on:

- no full-project sc

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# User Journey Execution Flow — local-fs Adapter

This document describes **how a single user command is executed internally**
when using the `local-fs` adapter, with a focus on:

- no full-project scans
- no caching or mirroring
- ephemeral, in-memory graph slices
- strict stateless CLI execution

The example command used throughout this document is:

```bash
work list   where kind=task and child_of=EPIC-42   order by priority desc   limit 5
```

Assumptions:
- active context: `local`
- tool: `local-fs`
- root directory: `.work/`
- project: `default`

---

## 1. Filesystem Ground Truth

```text
my-project/
└── .work/
    └── projects/
        └── default/
            ├── items/
            │   ├── EPIC-42.md
            │   ├── 0001.md
            │   ├── 0002.md
            │   └── 0003.md
            ├── links.json
            └── meta.json
```

Important properties:
- this is **not** a database
- files are not preloaded
- only accessed on demand

---

## 2. Command Parsing (No IO)

The CLI parses the command into an abstract syntax tree (AST).

```ts
ListCommand {
  type: "list",
  where: AND(
    EQ("kind", "task"),
    EQ("child_of", "EPIC-42")
  ),
  orderBy: { field: "priority", direction: "desc" },
  limit: 5
}
```

No filesystem access occurs at this stage.

---

## 3. Context Resolution

The active context is resolved.

```ts
Context {
  name: "local",
  tool: "local-fs",
  root: ".work",
  project: "default"
}
```

This defines the execution boundary.

---

## 4. Query Planning

The query planner determines the **minimal data requirements**.

```ts
QueryPlan {
  requiredKinds: ["task"],
  requiredRelations: ["child_of"],
  rootIds: ["EPIC-42"],
  requiredFields: ["priority"]
}
```

This plan guarantees no unnecessary filesystem access.

---

## 5. Adapter Resolution

The adapter registry selects the `LocalFsAdapter`.

```ts
const adapter = adapterRegistry.get("local-fs");
```

---

## 6. Relation Resolution (Filesystem Read #1)

The adapter resolves chil

*[truncated — see source for full prompt]*