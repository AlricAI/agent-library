# Custom Role Parsers

> Ltix parses standard LIS role URIs out of the box, but some platforms
send proprietary role vocabularies with their own URI namespaces. Without
a cust

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Custom Role Parsers

Ltix parses standard LIS role URIs out of the box, but some platforms
send proprietary role vocabularies with their own URI namespaces. Without
a custom parser, those URIs end up as raw strings in `unrecognized_roles`:

```elixir
context.claims.unrecognized_roles
#=> ["https://myplatform.example.com/roles/CourseAdmin"]
```

Register a custom role parser to teach Ltix how to handle them.

## Implementing the behaviour

A role parser is a module that implements `Ltix.LaunchClaims.Role.Parser`.
The only required callback is `parse/1`, which receives a role URI string
and returns `{:ok, %Role{}}` or `:error`:

```elixir
defmodule MyApp.Lti.PlatformRoleParser do
  use Ltix.LaunchClaims.Role.Parser

  alias Ltix.LaunchClaims.Role

  @base "https://myplatform.example.com/roles/"

  @roles %{
    "CourseAdmin" => :course_admin,
    "Facilitator" => :facilitator,
    "Grader" => :grader
  }

  @impl true
  def parse(uri) do
    suffix = String.replace_leading(uri, @base, "")

    case Map.fetch(@roles, suffix) do
      {:ok, name} ->
        {:ok, %Role{type: :context, name: name, sub_role: nil, uri: uri}}

      :error ->
        :error
    end
  end
end
```

The parser only receives URIs that match its registered prefix (see
[Registration](#registering-parsers) below), so you don't need to check
the prefix yourself.

## Optional: `to_uri/1`

If you need to convert `%Role{}` structs back to URI strings (e.g. for
building NRPS responses or test fixtures), implement the optional
`to_uri/1` callback:

```elixir
@roles_inverse Map.new(@roles, fn {k, v} -> {v, k} end)

@impl true
def to_uri(%Role{type: :context, name: name, sub_role: nil}) do
  case Map.fetch(@roles_inverse, name) do
    {:ok, suffix} -> {:ok, @base <> suffix}
    :error -> :error
  end
end

def to_uri(_), do: :error
```

## Registering parsers

Role parsers are registered as a map of URI prefix to parser module. The
prefix determines which URIs are routed to your parser. Ltix tries each
r

*[truncated — see source for full prompt]*