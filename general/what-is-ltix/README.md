# What Is Ltix

> Ltix is an Elixir library for handling LTI 1.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# What is Ltix?

Ltix is an Elixir library for handling LTI 1.3 launches on the tool side.
It takes care of the OIDC redirect flow, JWT signature verification, claim
parsing, and spec compliance so you can focus on what your tool actually
does.

## Why a library?

LTI 1.3 connects learning platforms (Canvas, Moodle, Blackboard) with
external tools (quiz engines, coding sandboxes, video players). When a
student clicks a link in their course, the platform launches the tool
through a multi-step browser redirect that tells the tool who the user
is, what course they're in, and what role they have.

The protocol is built on OpenID Connect and signed JWTs. Implementing it
correctly means handling:

- A three-step redirect flow with CSRF protection via state parameters
- JWKS fetching and caching to verify platform signatures
- JWT validation — signature, expiration, issuer, audience, nonce
- Claim parsing — roles, context, resource links, service endpoints
- Spec compliance across dozens of requirements from three IMS
  specifications

This is security-critical work with little room for error. Getting the
nonce check wrong opens you to replay attacks. Getting the audience
check wrong means accepting tokens meant for other tools.

## Two functions

Ltix collapses all of that into two function calls:

```elixir
# Step 1: Platform initiates login — build the redirect
{:ok, %{redirect_uri: url, state: state}} =
  Ltix.handle_login(params, launch_url)

# Step 2: Platform sends the signed JWT — validate and parse
{:ok, context} = Ltix.handle_callback(params, state)
```

The result is a `%Ltix.LaunchContext{}` containing everything about
the launch:

```elixir
context.claims.subject          #=> "user-12345"
context.claims.name             #=> "Jane Smith"
context.claims.email            #=> "jane@university.edu"
context.claims.roles            #=> [%Role{type: :context, name: :instructor}, ...]
context.claims.context          #=> %Context{id: "course-1", title: "Intro to Elixir"

*[truncated — see source for full prompt]*