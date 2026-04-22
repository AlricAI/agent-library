# Orchestrator Core

> ## Philosophy

The orchestrator is a **reliable, resilient, observable set of cooperating watchers**.

Everything else (APIs, UIs, configuration) exis

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Machinator v3: Orchestrator Core Design

## Philosophy

The orchestrator is a **reliable, resilient, observable set of cooperating watchers**.

Everything else (APIs, UIs, configuration) exists to:

1. Feed work into the system
2. Observe the system's state
3. Configure the system's behavior

---

## Agent States and Ownership

Each agent state is owned by exactly one watcher. Only the owner can transition OUT of that state.

```
┌─────────────────────────────────────────────────────────┐
│  State       │  Owner        │  Responsibility          │
├─────────────────────────────────────────────────────────┤
│  pending     │  SetupWatcher │  Worktree creation, env  │
│  ready       │  Assigner     │  Find work, assign task  │
│  assigned    │  AgentWatcher │  Run to completion/death │
└─────────────────────────────────────────────────────────┘
```

State transitions:

```
                    User requests new agent
                           │
                           ▼
                      ┌─────────┐
                      │ pending │ ◄──── SetupWatcher owns
                      └────┬────┘
                           │ setup complete
                           ▼
     ┌────────────────┌─────────┐◄───────────────┐
     │                │  ready  │ ◄──── Assigner │
     │                └────┬────┘        owns    │
     │                     │ task assigned       │
     │                     ▼                     │
     │               ┌──────────┐                │
     └───────────────│ assigned │ ◄──── Agent   │
       task done,    └──────────┘        Watcher │
       killed, or                        owns    │
       timed out     ────────────────────────────┘
```

No mutex needed - ownership rules prevent races:

- Assigner: only writes `ready` → `assigned`
- AgentWatcher: only writes `assigned` → `ready`
- SetupWatcher: only writes `pending` → `ready`

---

## Initialization

```go
func main() {
    state := loadState()

    go assigner(&state)
    go quotaW

*[truncated — see source for full prompt]*