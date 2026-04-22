# Testing

> Rules for testing applications that use Ltix.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Testing

Rules for testing applications that use Ltix.

## Test Configuration

Add to `config/test.exs`:

```elixir
config :ltix,
  storage_adapter: MyApp.LtiStorageAdapter,
  req_options: [plug: {Req.Test, :ltix}]
```

Point at your own storage adapter. The `req_options` plug routes all
outbound HTTP through `Req.Test`. Each internal module rewrites the plug
name to its own well-known stub name, so you can stub each independently:

| Stub name                       | HTTP call                         |
|---------------------------------|-----------------------------------|
| `Ltix.JWT.KeySet`               | JWKS public key fetches           |
| `Ltix.OAuth.ClientCredentials`  | OAuth token requests              |
| `Ltix.GradeService`            | Grade service (AGS) requests       |
| `Ltix.MembershipsService`      | Memberships (NRPS) requests        |

`setup_platform!/1` automatically stubs `Ltix.JWT.KeySet`.

## Platform Setup

In your test's `setup` block:

```elixir
setup do
  platform = Ltix.Test.setup_platform!(
    registration: fn reg ->
      jwk = MyApp.Lti.generate_jwk!()

      MyApp.Lti.create_registration!(%{
        issuer: reg.issuer,
        client_id: reg.client_id,
        auth_endpoint: reg.auth_endpoint,
        jwks_uri: reg.jwks_uri,
        token_endpoint: reg.token_endpoint,
        tool_jwk_id: jwk.id
      })
    end
  )

  %{platform: platform}
end
```

`setup_platform!/1` generates platform-side RSA keys, builds a registration
and deployment, and stubs the JWKS HTTP endpoint. Pass a `:registration`
function to create matching records in your persistence layer. Options:
`:issuer`, `:client_id`, `:deployment_id`.

## Three Test Patterns

### 1. Full OIDC Flow (Controller Tests)

Simulate the complete platform-initiated launch through your routes:

```elixir
test "launch renders dashboard", %{conn: conn, platform: platform} do
  conn = post(conn, ~p"/lti/login", Ltix.Test.login_params(platform))

  state = get_session(conn, :lti_stat

*[truncated — see source for full prompt]*