# Future Features

> Features deferred from v0 but planned for future releases.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Future Features 🔮

Features deferred from v0 but planned for future releases.

## Interactive Agent Enhancements

### Multiple Choice Options
**Status**: Deferred (v0 uses simple wait_for_user())

Allow InteractiveAgent to present structured choices:

```python
wait_for_user(
    prompt="What do you do?",
    choices=[
        {"id": "explore", "text": "Explore the castle"},
        {"id": "talk", "text": "Talk to the wizard"},
        {"id": "leave", "text": "Leave the area"}
    ]
)
```

**UI Impact:**
- Display choices as buttons in Agent View
- Store choice ID in user_message log entry
- Agent receives structured choice data

**Benefits:**
- Better UX than free text
- Agent can branch on specific choices
- Clearer intent tracking

---

## Context Management

### Auto-Summarization
**Status**: Planned (post-v0)

When agent context approaches 200k characters:
1. Trigger summarization tool
2. Agent generates summary of conversation
3. Compress old messages into summary
4. Continue with reduced context

**Implementation:**
```python
# When context > 200k chars
summary = agent.summarize_conversation(start_idx=0, end_idx=100)
# Replace old messages with summary
agent.messages = [
    system_message,
    {"role": "assistant", "content": f"[Summary of earlier conversation: {summary}]"},
    ...recent_messages
]
```

**Benefits:**
- Longer-running agents
- Cost reduction
- Maintain coherence over time

---

## Agent Communication

### Inter-Agent Messaging
**Status**: Future exploration

Allow agents to send messages to each other:

```python
# Tool: send_agent_message
send_agent_message(
    target_agent_id="writer-001",
    message="I found new character info: Merlin is actually 500 years old"
)
```

**Use Cases:**
- Researcher → Writer: "Found these sources"
- Reader → Interactive: "New character discovered"
- Writer → Reader: "Need more info about X"

**Challenges:**
- Message routing
- Context injection
- Loop prevention

---

## Researcher & Recorder Agents

###

*[truncated — see source for full prompt]*