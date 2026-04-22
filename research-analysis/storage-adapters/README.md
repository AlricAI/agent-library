# Storage Adapters

> Ltix doesn't assume your database, ORM, or persistence strategy.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Storage Adapters

Ltix doesn't assume your database, ORM, or persistence strategy. Your
application owns all storage and provides lookups through the
`Ltix.StorageAdapter` behaviour. This guide covers what each callback
does, how to build a production-ready implementation with Ecto, and
common pitfalls.

## Callback overview

| Callback | When it's called | What it does |
|---|---|---|
| `get_registration/2` | Login initiation | Look up a platform by issuer and optional client_id |
| `get_deployment/2` | Launch validation | Look up a deployment by registration and deployment_id |
| `store_nonce/2` | Login initiation | Persist a nonce for later verification |
| `validate_nonce/2` | Launch validation | Verify a nonce was issued by us, then consume it |

## Registration lookups

```elixir
@callback get_registration(issuer :: String.t(), client_id :: String.t() | nil) ::
            {:ok, Registerable.t()} | {:error, :not_found}
```

Return any struct that implements `Ltix.Registerable`. The library
extracts the `Ltix.Registration` it needs via the protocol, and
your original struct is preserved in the `Ltix.LaunchContext` — so
you can access your own fields (database IDs, tenant info, etc.)
after a successful launch without an extra query.

The `client_id` may be `nil` — some platforms don't include it in the
login initiation request. Your adapter must handle both cases:

```elixir
def get_registration(issuer, nil) do
  case Repo.get_by(PlatformRegistration, issuer: issuer) do
    nil -> {:error, :not_found}
    record -> {:ok, record}
  end
end

def get_registration(issuer, client_id) do
  case Repo.get_by(PlatformRegistration, issuer: issuer, client_id: client_id) do
    nil -> {:error, :not_found}
    record -> {:ok, record}
  end
end
```

Your Ecto schema implements `Ltix.Registerable` to map its fields:

```elixir
defimpl Ltix.Registerable, for: MyApp.Lti.PlatformRegistration do
  def to_registration(record) do
    Ltix.Registration.new(%{
      issuer: record.i

*[truncated — see source for full prompt]*