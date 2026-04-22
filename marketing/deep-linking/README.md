# Deep Linking

> Deep linking lets a platform ask your tool to select content.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Deep Linking

Deep linking lets a platform ask your tool to select content. Instead
of launching directly into an activity, the platform sends an
`LtiDeepLinkingRequest` and your tool responds with one or more content
items the platform should link to. This guide covers handling deep
linking launches, building content items, and sending responses back
to the platform.

## Handling a deep linking launch

Deep linking requests arrive through the same OIDC flow as regular
launches. Your existing login and launch endpoints work without
changes. The difference is in `message_type`:

```elixir
def launch(conn, params) do
  state = get_session(conn, :lti_state)
  {:ok, context} = Ltix.handle_callback(params, state)

  case context.claims.message_type do
    "LtiDeepLinkingRequest" ->
      settings = context.claims.deep_linking_settings

      conn
      |> assign(:context, context)
      |> assign(:settings, settings)
      |> render(:content_picker)

    "LtiResourceLinkRequest" ->
      conn
      |> assign(:context, context)
      |> render(:launch)
  end
end
```

The `deep_linking_settings` struct tells you what the platform accepts:

```elixir
settings.accept_types
# => ["ltiResourceLink", "link"]

settings.accept_multiple
# => true

settings.accept_lineitem
# => true
```

Use these to tailor your selection UI. For example, hide the "create
assignment" option if `"ltiResourceLink"` is not in `accept_types`.

## Building content items

The most common content item is an LTI resource link, which tells the
platform to create a link that launches back into your tool:

```elixir
{:ok, link} = Ltix.DeepLinking.ContentItem.LtiResourceLink.new(
  url: "https://tool.example.com/activities/123",
  title: "Chapter 3 Quiz"
)
```

Five content item types are available:

| Type | Module | When to use |
|------|--------|-------------|
| `ltiResourceLink` | `Ltix.DeepLinking.ContentItem.LtiResourceLink` | Activity that launches back into your tool |
| `link` | `Ltix.DeepLinking.Co

*[truncated — see source for full prompt]*