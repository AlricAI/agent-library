# Memberships Service

> When your tool needs to know who is enrolled in a course, use the
memberships service to fetch the roster from the platform. This guide
covers common 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Memberships Service

When your tool needs to know who is enrolled in a course, use the
memberships service to fetch the roster from the platform. This guide
covers common patterns for working with rosters in your application.

## Fetching the roster after launch

Authenticate from the launch context and fetch the roster in your
controller:

```elixir
def launch(conn, params) do
  state = get_session(conn, :lti_state)
  {:ok, context} = Ltix.handle_callback(params, state)

  {:ok, client} = Ltix.MembershipsService.authenticate(context)
  {:ok, roster} = Ltix.MembershipsService.get_members(client)

  active_learners =
    roster
    |> Enum.filter(fn m -> m.status == :active end)
    |> Enum.filter(fn m -> Ltix.LaunchClaims.Role.learner?(m.roles) end)

  conn
  |> assign(:learners, active_learners)
  |> assign(:course_title, roster.context.title)
  |> render(:launch)
end
```

Not all launches include the memberships endpoint. If the platform
didn't include it, `authenticate/2` returns a `ServiceNotAvailable`
error. Check for this if your tool should still work without roster
access:

```elixir
case Ltix.MembershipsService.authenticate(context) do
  {:ok, client} ->
    {:ok, roster} = Ltix.MembershipsService.get_members(client)
    # use roster

  {:error, %Ltix.Errors.Invalid.ServiceNotAvailable{}} ->
    # roster not available for this launch
end
```

## Syncing rosters in the background

For scheduled syncs or Oban workers, store the endpoint URL during
the first launch and authenticate from a registration later:

```elixir
# During launch: save the endpoint URL
url = context.claims.memberships_endpoint.context_memberships_url
MyApp.Courses.store_memberships_url(course_id, url)
```

```elixir
# In a background job
alias Ltix.LaunchClaims.MembershipsEndpoint

def perform(%{args: %{"course_id" => course_id}}) do
  registration = MyApp.Courses.get_registration(course_id)
  url = MyApp.Courses.get_memberships_url(course_id)

  {:ok, client} = Ltix.MembershipsService.

*[truncated — see source for full prompt]*