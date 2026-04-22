# Streaming Orchestration

> > Event-driven turn loops let you observe and control agent execution in real time.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Streaming Orchestration

> Event-driven turn loops let you observe and control agent execution in real time.

## The Problem

You send a prompt and wait. You don't know if the agent is stuck, hallucinating, or burning through tokens on the wrong task. When something goes wrong, you can't tell where. Budget overruns happen silently.

## The Pattern

Replace fire-and-wait with a **typed event stream**. Every meaningful state transition emits a structured event. Your harness consumes events, enforces budgets, compacts history, and halts cleanly when limits are hit.

### Turn Event Types

```
message_start       → agent received the prompt, turn begins
command_match       → agent identified a slash command to run
tool_match          → agent identified a tool call
permission_denial   → a tool call was blocked by permission context
message_delta       → streaming text output chunk
message_stop        → turn complete, reason included
```

Handle only what you need. Ignore the rest.

### Minimal Turn Loop

```python
def run_turn(session, prompt):
    for event in session.stream_submit_message(prompt):
        match event["type"]:
            case "tool_match":
                if session.permissions.blocks(event["name"]):
                    log_denial(event)
                    continue
                dispatch_tool(event)
            case "message_delta":
                print(event["text"], end="", flush=True)
            case "message_stop":
                session.record_turn(event)
                return event["stop_reason"]
```

### Turn Budgeting

Set hard limits before the turn starts. Check them after each event. Stop cleanly rather than letting the model run indefinitely.

```python
@dataclass
class TurnBudget:
    max_turns: int = 10
    max_input_tokens: int = 50_000
    max_output_tokens: int = 20_000

    def exhausted(self, usage: TokenUsage) -> bool:
        return (
            usage.turns >= self.max_turns
            or usage.input_tokens >= self.max_in

*[truncated — see source for full prompt]*