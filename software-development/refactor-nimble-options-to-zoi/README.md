# Refactor Nimble Options To Zoi

> ## Context

The project already has `zoi ~> 0.17` as a dependency but uses NimbleOptions
for all option validation (15 schemas across 6 modules). Zoi'

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Refactor: NimbleOptions → Zoi

## Context

The project already has `zoi ~> 0.17` as a dependency but uses NimbleOptions
for all option validation (15 schemas across 6 modules). Zoi's `keyword/2`
type is a near-direct replacement for NimbleOptions' keyword list validation,
and `Zoi.describe/1` replaces `NimbleOptions.docs/1` for documentation
generation. This migration unifies on a single validation library and removes
NimbleOptions.

**Why Zoi over NimbleOptions?**
- Richer type system (unions, enums, structs, dynamic maps) with chainable API
- Built-in refinements (`positive()`, `non_negative()`, `min()`, `max()`)
  replace hand-rolled custom validators
- `Zoi.type_spec/1` auto-generates `@type` specs from schemas
- `Zoi.describe/1` replaces `NimbleOptions.docs/1` for doc generation
- `Zoi.codec/3` enables bidirectional parsing (decode keyword → struct,
  encode struct → keyword/map) for data transfer types
- Already a dependency — removing NimbleOptions reduces dep count

---

## 1. Translation Reference

### 1.1 Schema Definition

```elixir
# Before
@schema NimbleOptions.new!(
  name: [type: :string, required: true, doc: "The name."],
  count: [type: :pos_integer, default: 10, doc: "Page size."]
)

# After
@schema Zoi.keyword(
  name: Zoi.string(description: "The name.") |> Zoi.required(),
  count: Zoi.integer(description: "Page size.", gt: 0) |> Zoi.default(10)
)
```

### 1.2 Type Mappings

| NimbleOptions                          | Zoi                                            |
|----------------------------------------|------------------------------------------------|
| `type: :string`                        | `Zoi.string()`                                 |
| `type: :boolean`                       | `Zoi.boolean()`                                |
| `type: :atom`                          | `Zoi.atom()`                                   |
| `type: :pos_integer`                   | `Zoi.integer() \|> Zoi.positive()`             |
| `type: :keyword_list`     

*[truncated — see source for full prompt]*