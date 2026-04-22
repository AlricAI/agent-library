# Registerable Protocol

> **Scope**: Introduce `Ltix.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Registerable & Deployable Protocols

**Scope**: Introduce `Ltix.Registerable` and `Ltix.Deployable` protocols so
that host apps can return their own structs from `StorageAdapter` callbacks.
The library extracts `Registration` and `Deployment` data via protocol
dispatch; `LaunchContext` holds the user's original structs.

**Motivation**: Today the user must manually construct `%Registration{}` and
`%Deployment{}` in their storage adapter, which is error-prone. After launch,
`LaunchContext` holds only Ltix's internal structs — the user's own data (DB
IDs, tenant associations, etc.) is lost, forcing an extra query to reconnect
with their records.

**Design decisions**:

- Two protocols (`Registerable`, `Deployable`), not one combined protocol —
  they operate on different structs from different callbacks.
- `LaunchContext.registration` and `.deployment` hold the user's original
  structs (whatever implements the protocol). Ltix calls the protocol
  internally whenever it needs `Registration.t()` or `Deployment.t()`.
- Identity implementations for `Ltix.Registration` and `Ltix.Deployment`
  keep test helpers and internal code working without wrapping.
- `StorageAdapter` callback return types become protocol-typed.
- The nonce callbacks (`store_nonce`, `validate_nonce`) still receive
  `Registration.t()` — the library resolves the protocol before calling them.
  This avoids forcing users to implement `Registerable` just to handle nonces.
- `OAuth.Client` stores `Registration.t()` (resolved), not the user's struct.
  OAuth is an internal concern; the user's struct doesn't belong there.

---

## Phase 1 — Protocols and Identity Implementations

Define the protocols and implement them for the existing Ltix structs.

### 1.1 `Ltix.Registerable` protocol

Create `lib/ltix/registerable.ex`:

```elixir
defprotocol Ltix.Registerable do
  @spec to_registration(t()) :: {:ok, Ltix.Registration.t()} | {:error, Exception.t()}
  def to_registration(source)
end
```

- Single function

*[truncated — see source for full prompt]*