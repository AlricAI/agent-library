# Advantage Services

> Rules for working with LTI Advantage Services: Grade Service (AGS), Memberships Service
(NRPS), and OAuth token management.

## Authenticate-Then-Call

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Advantage Services

Rules for working with LTI Advantage Services: Grade Service (AGS), Memberships Service
(NRPS), and OAuth token management.

## Authenticate-Then-Call Pattern

All services follow the same pattern:

```elixir
{:ok, client} = Ltix.GradeService.authenticate(context)
{:ok, items} = Ltix.GradeService.list_line_items(client)
```

`authenticate/2` returns an `%OAuth.Client{}` with the access token and endpoints baked in.
Pass the client to all subsequent service calls.

You can also authenticate from a `%Registration{}` directly (for background jobs):

```elixir
{:ok, client} = Ltix.MembershipsService.authenticate(registration, endpoint: endpoint)
```

## Service Availability

Services are optional per-launch. **Always** handle `ServiceNotAvailable`:

```elixir
case Ltix.GradeService.authenticate(context) do
  {:ok, client} -> # use it
  {:error, %Ltix.Errors.Invalid.ServiceNotAvailable{}} -> # degrade gracefully
end
```

## Token Lifecycle

- Tokens typically last ~1 hour. Safe to ignore for single request handlers.
- For background jobs, check expiry before each call:

```elixir
client = if Ltix.OAuth.Client.expired?(client), do: Ltix.OAuth.Client.refresh!(client), else: client
```

- Tokens are scoped to a registration (platform + client_id), not a course. Reuse across
  courses on the same platform with `Client.with_endpoints/2`.
- Platforms may grant fewer scopes than requested. Service functions validate automatically
  and return `ScopeMismatch` if the required scope is missing.

## Grade Service

### Posting Scores

```elixir
{:ok, score} = Ltix.GradeService.Score.new(
  user_id: context.claims.subject,
  score_given: 85,
  score_maximum: 100,
  activity_progress: :completed,
  grading_progress: :fully_graded
)

:ok = Ltix.GradeService.post_score(client, score)
```

- `Score.new/1` validates fields and auto-generates `:timestamp` if omitted.
- **Only `:fully_graded`** guarantees the grade appears in the platform's gradebook. Other
  grading p

*[truncated — see source for full prompt]*