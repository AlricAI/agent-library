# Advantage Services

> After a successful launch, your tool can call back into the platform
to query rosters, post grades, or manage content. These platform APIs
are called 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Advantage Services

After a successful launch, your tool can call back into the platform
to query rosters, post grades, or manage content. These platform APIs
are called Advantage services. This guide covers authenticating to
them and managing tokens in your application.

## Calling a service after launch

A launch gives you a `%LaunchContext{}` containing the platform's
service endpoints. Authenticate and call a service directly in your
controller:

```elixir
def launch(conn, params) do
  state = get_session(conn, :lti_state)
  {:ok, context} = Ltix.handle_callback(params, state)

  # Authenticate to the memberships service
  case Ltix.MembershipsService.authenticate(context) do
    {:ok, client} ->
      {:ok, roster} = Ltix.MembershipsService.get_members(client)

      conn
      |> assign(:roster, roster)
      |> assign(:context, context)
      |> render(:launch)

    {:error, %Ltix.Errors.Invalid.ServiceNotAvailable{}} ->
      # Platform didn't include the memberships endpoint in this launch
      conn
      |> assign(:roster, nil)
      |> assign(:context, context)
      |> render(:launch)
  end
end
```

Each service provides an `authenticate/2` shorthand that extracts the
endpoint from launch claims and acquires a token in one step. See
[Memberships Service](memberships-service.md) for the full roster API.

## Background service calls

Outside of a launch, you won't have a `%LaunchContext{}`. Instead,
authenticate directly with a registration and a stored endpoint URL:

```elixir
alias Ltix.LaunchClaims.MembershipsEndpoint

endpoint = MembershipsEndpoint.new(stored_memberships_url)

{:ok, client} = Ltix.MembershipsService.authenticate(registration,
  endpoint: endpoint
)

{:ok, roster} = Ltix.MembershipsService.get_members(client)
```

Store the endpoint URL when you first see it during a launch, then
use it later in background jobs:

```elixir
# During launch: save the endpoint URL for later
url = context.claims.memberships_endpoint.context_memberships_u

*[truncated — see source for full prompt]*