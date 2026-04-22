# Grade Service

> When your tool needs to send grades back to the platform or manage
gradebook columns, use the grade service (Assignment and Grade
Services, or AGS). T

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Grade Service

When your tool needs to send grades back to the platform or manage
gradebook columns, use the grade service (Assignment and Grade
Services, or AGS). This guide covers the two main workflows for
working with grades in your application.

## Posting a score after launch

The simplest case: the platform created a gradebook column (line item)
for your resource link, and you just need to post a score. Authenticate
from the launch context and post directly:

```elixir
def launch(conn, params) do
  state = get_session(conn, :lti_state)
  {:ok, context} = Ltix.handle_callback(params, state)

  {:ok, score} = Ltix.GradeService.Score.new(
    user_id: context.claims.subject,
    score_given: 85,
    score_maximum: 100,
    activity_progress: :completed,
    grading_progress: :fully_graded
  )

  {:ok, client} = Ltix.GradeService.authenticate(context)
  :ok = Ltix.GradeService.post_score(client, score)

  conn
  |> put_flash(:info, "Grade submitted")
  |> redirect(to: ~p"/assignments")
end
```

Not all launches include the grade service endpoint. If the platform
didn't include it, `authenticate/2` returns a `ServiceNotAvailable`
error:

```elixir
case Ltix.GradeService.authenticate(context) do
  {:ok, client} ->
    :ok = Ltix.GradeService.post_score(client, score)

  {:error, %Ltix.Errors.Invalid.ServiceNotAvailable{}} ->
    # Grade passback not available for this launch
end
```

See [Building Scores](cookbooks/score-construction.md) for progress
tracking, extra credit, comments, and choosing progress values.

## Managing line items

When your tool needs multiple gradebook columns per resource link, or
wants to create columns on its own, use the **programmatic** workflow:

```elixir
{:ok, client} = Ltix.GradeService.authenticate(context)

{:ok, quiz_item} = Ltix.GradeService.create_line_item(client,
  label: "Quiz 1",
  score_maximum: 100,
  tag: "quiz"
)

:ok = Ltix.GradeService.post_score(client, score, line_item: quiz_item)
```

Fetch a line item before up

*[truncated — see source for full prompt]*