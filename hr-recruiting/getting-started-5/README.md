# Getting Started

> This guide walks you through adding LTI 1.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Getting Started

This guide walks you through adding LTI 1.3 launch support to a Phoenix
application. By the end, your app will handle launches from Canvas,
Moodle, Blackboard, or any other LTI 1.3 platform. You'll also have a
clear list of what's left to get it production-ready.

You'll need an existing Phoenix app with Ecto. If you'd like to
understand the protocol before diving in, read [LTI Advantage
Concepts](concepts.md) first.

## Installation

### Add the dependency

```elixir
# mix.exs
defp deps do
  [
    {:ltix, "~> 0.1"}
  ]
end
```

Run `mix deps.get` to fetch the package.

### Start the key cache

Ltix caches platform public keys in ETS so it doesn't re-fetch them on
every launch. Add the cache to your supervision tree:

```elixir
# lib/my_app/application.ex
children = [
  # ... your existing children (Repo, Endpoint, etc.)
  Ltix.JWT.KeySet.EtsCache
]
```

> #### Cachex alternative {: .tip}
>
> If you already use Cachex, you can use `Ltix.JWT.KeySet.CachexCache`
> instead. See `Ltix.JWT.KeySet.CachexCache` for setup instructions.

## Database schema

You need tables for four LTI concerns (signing keys, registrations,
deployments, and replay-prevention tokens) plus application tables for
users and courses. All the LTI schemas live under a `MyApp.Lti` context.

### Migration

```elixir
# priv/repo/migrations/XXXXXXXXXXXXXX_create_lti_tables.exs
defmodule MyApp.Repo.Migrations.CreateLtiTables do
  use Ecto.Migration

  def change do
    create table(:lti_jwks) do
      add :private_key_pem, :text, null: false
      add :kid, :string, null: false
      add :active, :boolean, default: true, null: false
      timestamps()
    end

    create unique_index(:lti_jwks, [:kid])

    create table(:lti_registrations) do
      add :issuer, :string, null: false
      add :client_id, :string, null: false
      add :auth_endpoint, :string, null: false
      add :jwks_uri, :string, null: false
      add :token_endpoint, :string
      add :jwk_id, references(:lti_jwks

*[truncated — see source for full prompt]*