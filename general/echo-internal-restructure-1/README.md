# Echo Internal Restructure

> ## Goal

Restructure `@dxos/echo` `src/internal/` directory so that its subdirectory structure mirrors the exported API modules (Obj, Ref, Annotation,

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ECHO Internal Directory Restructure

## Goal

Restructure `@dxos/echo` `src/internal/` directory so that its subdirectory structure mirrors the exported API modules (Obj, Ref, Annotation, etc.), without changing any behavior.

Each API module will import from its own internal subdirectory:

```ts
// Obj.ts
import * as objInternal from './internal/Obj';
```

Modules that don't map cleanly to a single API module go in `internal/common/`.

## Rules

1. **common/ must not import from non-common modules.** The dependency direction is:
   `Annotation/`, `Entity/`, `Obj/`, `Ref/`, etc. → `common/` (never the reverse).
   `common/` is the shared foundation; non-common modules depend on it.
2. `internal/index.ts` must continue to re-export everything (backward compat for `@dxos/echo/internal`).
3. No behavioral changes — only file moves and import path updates.
4. Each internal subdir must NOT create circular imports with common/.

## Final Structure

```
internal/
  Annotation/      ← annotations + sorting helpers
  Entity/          ← entity model, api helpers (getDXN, getDatabase), version
  Format/          ← format definitions
  JsonSchema/      ← json-schema conversion
  Obj/             ← object operations (create, clone, snapshot, serialization)
  Ref/             ← references
  Type/            ← echo schema (EchoSchema, compose, persistent)
  common/
    api/           ← meta helpers only (getMetaChecked, getKeys, addTag, etc.)
    proxy/         ← proxy/reactivity (make-object, reactive, change-context, etc.)
    types/         ← base types, entity kinds, model symbols, meta, typename, version
  index.ts         ← re-exports everything (backward compat)
```

## API Module → Internal Import Mapping

| API Module    | Internal import                         |
| ------------- | --------------------------------------- |
| Annotation.ts | `./internal/Annotation`                 |
| Entity.ts     | `./internal/Entity` + `./internal`      |
| Format.ts     | `./internal

*[truncated — see source for full prompt]*