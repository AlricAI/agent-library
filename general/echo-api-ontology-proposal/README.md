# Echo Api Ontology Proposal

> Moved from `packages/core/echo/echo/API.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ECHO API Ontology Proposal

Moved from `packages/core/echo/echo/API.md` on 2026-03-09.

## Principles

- Separation of APIs to work with data (Entity, Obj, Relation, Feed) and APIs to introspect schema (Type). **DONE**
- Symetry of names used to define schema, and names used to specify TypeScript types. **DONE**

```ts
const Mailbox = Schema.Struct({
  messages: Ref.Ref(Feed.Feed)
}).pipe(Type.object({ typename: 'example.com/type/Mailbox', version: '0.1.0' }));
interface Mailbox extends Schema.Schema.Type<typeof Mailbox> {}

typeof mailbox.messages === Feed.Feed;

const Collection = Schema.Struct({
  objects: Schema.Array(Ref.Ref(Obj.Unknown))
}).pipe(Type.relation({ typename: 'example.com/type/Collection', version: '0.1.0' }));
interface Collection extends Schema.Schema.Type<typeof Collection> {}

typeof collection.objects === Obj.Unknown[];

const feed = Feed.make({});
typeof feed === Feed.Feed;
```

- Entity module defines APIs useful for both objects and relations, but Obj and Relation can specialize and alias those APIs. **DONE**
- Snaphots are deined as a higher-order type so that a snapshot type can be derived any type. **DONE**

```ts
Entity.Snapshot<Person>;
Entity.Snapshot<Relation.AnchoredTo>;
Entity.Snapshot<Obj.Unknown>;
Entity.Snapshot<Entity.Unknown>;
```

- Snapshots cannot be mutated or used with `db.add` or `db.remove`. **DONE** (snapshots are branded with `SnapshotKindId` and are structurally incompatible with mutable APIs)

## `Type` module

Used when working with the schema definitions

Two use-cases:

- Definiting new schema.
- Iterating and introspecting schema.

The types are used when dealing with schema as values.

Types:

- type `Type.Entity<T extends Entity.Unknown>` - instance of a schema for an object or relation of instance type `T`. **NOT DONE** (no `Type.Entity<T>` exists; `Type.AnyEntity` is the union of `AnyObj | AnyRelation`)
- type `Type.UnknownEntity` - instance of a schema for object or relation, but instance type is not know

*[truncated — see source for full prompt]*