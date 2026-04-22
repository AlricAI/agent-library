# Custom Claim Parsers

> Ltix parses standard OIDC and LTI claims from the launch JWT
automatically. Any unrecognized claims land in the `extensions` map as
raw values:

```el

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Custom Claim Parsers

Ltix parses standard OIDC and LTI claims from the launch JWT
automatically. Any unrecognized claims land in the `extensions` map as
raw values:

```elixir
context.claims.extensions
#=> %{"https://myplatform.example.com/claim/analytics" => %{"session_id" => "abc123"}}
```

Register custom claim parsers to transform these raw values into
structured data.

## Writing a claim parser

A claim parser is any function that takes a raw claim value and returns
`{:ok, parsed}` or `{:error, reason}`. There is no behaviour to
implement:

```elixir
defmodule MyApp.Lti.AnalyticsClaim do
  defstruct [:session_id, :tracking_enabled]

  def parse(%{"session_id" => session_id} = raw) do
    {:ok,
     %__MODULE__{
       session_id: session_id,
       tracking_enabled: Map.get(raw, "tracking_enabled", false)
     }}
  end

  def parse(_), do: {:error, "missing session_id in analytics claim"}
end
```

## Registering parsers

Claim parsers are registered as a map of claim key to parser function.
The key is the full claim name as it appears in the JWT (usually a
namespaced URI for extension claims).

**Via application config** (recommended for parsers that apply globally):

```elixir
# config/config.exs
config :ltix, Ltix.LaunchClaims,
  claim_parsers: %{
    "https://myplatform.example.com/claim/analytics" =>
      &MyApp.Lti.AnalyticsClaim.parse/1
  }
```

**Via `handle_callback/3`** (for per-call control):

```elixir
Ltix.handle_callback(params, state,
  claim_parsers: %{
    "https://myplatform.example.com/claim/analytics" =>
      &MyApp.Lti.AnalyticsClaim.parse/1
  }
)
```

**Via `LaunchClaims.from_json/2`** (for direct parsing):

```elixir
Ltix.LaunchClaims.from_json(claims,
  parsers: %{
    "https://myplatform.example.com/claim/analytics" =>
      &MyApp.Lti.AnalyticsClaim.parse/1
  }
)
```

Per-call parsers merge with application config, with per-call taking
priority for overlapping keys.

## Accessing parsed claims

Parsed extension claims remain in the

*[truncated — see source for full prompt]*