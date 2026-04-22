# Error Handling

> When a launch fails, you need to know what went wrong and how to
respond. Ltix returns `{:error, exception}` from both `handle_login/3`
and `handle_ca

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Error Handling

When a launch fails, you need to know what went wrong and how to
respond. Ltix returns `{:error, exception}` from both `handle_login/3`
and `handle_callback/3`, with errors organized into three classes using
[Splode](https://hexdocs.pm/splode). You can match on the category
without knowing every individual error type.

## Error classes

| Class | Module | Meaning |
|---|---|---|
| `:invalid` | `Ltix.Errors.Invalid` | Bad input — malformed JWT, missing claims, unknown registration |
| `:security` | `Ltix.Errors.Security` | Security violation — bad signature, expired token, nonce replay |
| `:unknown` | `Ltix.Errors.Unknown` | Unexpected failure — network errors, bugs |

## HTTP status codes

Every error carries an HTTP status code derived from its class:

| Class | Status |
|---|---|
| `:invalid` | 400 |
| `:security` | 401 |
| `:unknown` | 500 |

Use `Ltix.Errors.status_code/1` to get it:

```elixir
case Ltix.handle_callback(params, state) do
  {:ok, context} ->
    handle_launch(conn, context)

  {:error, error} ->
    conn
    |> put_status(Ltix.Errors.status_code(error))
    |> text(Exception.message(error))
end
```

### Plug.Exception

If your application depends on Plug, Ltix errors automatically implement
the `Plug.Exception` protocol. Phoenix error views and `Plug.Debugger`
pick up the correct status code without any extra work on your part.

## Matching on class

Every Ltix error struct has a `class` field you can match on for
different handling per category:

```elixir
case Ltix.handle_callback(params, state) do
  {:ok, context} ->
    handle_launch(conn, context)

  {:error, error} ->
    status = Ltix.Errors.status_code(error)

    case error.class do
      :invalid ->
        conn |> put_status(status) |> text("Bad request: #{Exception.message(error)}")

      :security ->
        conn |> put_status(status) |> text("Unauthorized: #{Exception.message(error)}")

      :unknown ->
        Logger.error("LTI launch failed: #{Exception.messag

*[truncated — see source for full prompt]*