# Compiler Ir

> A compact, validated graph the compiler emits from the DSL for fast runtime execution and sharing.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Compiler IR (Intermediate Representation)

A compact, validated graph the compiler emits from the DSL for fast runtime execution and sharing.

## Goals

- Deterministic build, stable IDs for node/edge sharing
- Minimal runtime decoding; direct execution
- BSSN: only fields used now

## Core Types (skeletal)

- Network
  - version :: term
  - nodes :: %{node_id => Node}
  - edges :: [%Edge]
  - entrypoints :: [node_id]
  - metadata :: %{selectivity_hints?: boolean}
- Node (tagged union)
  - :alpha_test
    - tests :: [Predicate]
    - out_memory :: memory_id
  - :alpha_memory
    - key :: AlphaKey
  - :join
    - left :: input_ref
    - right :: input_ref
    - on :: [JoinCond]
    - out_memory :: memory_id
  - :neg_exists
    - mode :: :not | :exists
    - left :: input_ref
    - right :: input_ref
  - :accumulate
    - from :: input_ref
    - group_by :: [Binding]
    - reducers :: [Reducer]
  - :production
    - rule_id :: String.t()
    - salience :: integer
    - refraction :: :default | :none
    - rhs :: [Action]
- Edge
  - from :: node_id
  - to :: node_id
  - bindings :: %{var => source}

## Predicates and Joins (minimal)

- Predicate
  - field :: Path.t()
  - op :: :eq | :gt | :lt | :ge | :le | :in | :match
  - value :: literal | var
- JoinCond
  - left :: var_or_field
  - op :: :eq
  - right :: var_or_field

## Memories/Indexes

- memory_id :: integer
- alpha indexes: %{AlphaKey => hash_spec}
- beta indexes: %{[vars] => hash_spec}

## Actions

- :emit, module, fields :: %{atom => Expr}
- :call, {mod, fun, args :: [Expr]} (internal only)
- :log, level, msg :: Expr

## Expr (subset)

- literal | var | {op, [Expr]}

## Stability

- node_id, memory_id allocated deterministically from normalized LHS
- rule_id carried from DSL

## Out of Scope (now)

- codegen modules
- advanced predicate ops beyond equality/range
- distributed links