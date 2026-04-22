# Working With Roles

> LTI platforms send role URIs in the launch JWT.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Working with Roles

LTI platforms send role URIs in the launch JWT. Ltix parses these into
structured `%Role{}` structs with predicates and filters for
authorization logic. Most tools just need the predicates in the next
section.

## Checking roles

The most common check is "is this user an instructor or a learner?"

```elixir
alias Ltix.LaunchClaims.Role

Role.instructor?(context.claims.roles)
Role.learner?(context.claims.roles)
Role.administrator?(context.claims.roles)
Role.content_developer?(context.claims.roles)
Role.mentor?(context.claims.roles)
Role.teaching_assistant?(context.claims.roles)
```

Predicates match on the role **name**, including sub-roles. So
`instructor?/1` returns `true` for both a principal Instructor and
an Instructor#TeachingAssistant. To check for only the principal role,
see [Sub-roles](#sub-roles) below.

These check **context** roles only. An institution-level
`:administrator` won't match `Role.administrator?/1`. Use
`has_role?/4` for [cross-type checks](#generic-checks-with-has_role-4).

## Roles in launch claims

After a successful launch, roles are available on the claims struct:

```elixir
{:ok, context} = Ltix.handle_callback(params, state)

context.claims.roles
#=> [%Role{type: :context, name: :instructor, ...}]

context.claims.unrecognized_roles
#=> ["http://example.com/custom-role"]
```

Recognized role URIs become `%Role{}` structs. Anything the parser
doesn't recognize goes into `unrecognized_roles` as raw URI strings.

## Building authorization logic

A typical pattern for an LTI tool:

```elixir
defmodule MyAppWeb.LtiAuth do
  alias Ltix.LaunchClaims.Role

  def authorize(context) do
    roles = context.claims.roles

    cond do
      Role.administrator?(roles) -> :admin
      Role.teaching_assistant?(roles) -> :ta
      Role.instructor?(roles) -> :instructor
      Role.learner?(roles) -> :learner
      true -> :observer
    end
  end
end
```

Use the result to gate access in your controller:

```elixir
def launch(conn, pa

*[truncated — see source for full prompt]*