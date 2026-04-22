# SDK AGENT GENERATOR PLAN

> ## Objective

Transform the goal-seeking agent generator to produce agents using real AI SDKs
(Claude Agent SDK, GitHub Copilot SDK, Microsoft Agent F

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# SDK-Based Goal-Seeking Agent Generator Plan

## Objective

Transform the goal-seeking agent generator to produce agents using real AI SDKs
(Claude Agent SDK, GitHub Copilot SDK, Microsoft Agent Framework) with the
learning/teaching/applying architecture from the eval harness.

## Architecture

```
amplihack new --sdk copilot --file prompt.md
  │
  ├── GoalSeekingAgent (ABC) ─── shared interface
  │     ├── 7 learning tools (learn, search, explain, gaps, verify, store, summary)
  │     ├── amplihack-memory-lib (Kuzu)
  │     ├── Goal-seeking behavior (intent → goal → plan → iterate → evaluate)
  │     └── Eval harness integration (optional)
  │
  ├── CopilotGoalSeekingAgent ─── github-copilot-sdk
  │     ├── Native: file system, git, web (--allow-all)
  │     ├── Session-based state
  │     └── MCP integration
  │
  ├── ClaudeGoalSeekingAgent ─── claude-agents
  │     ├── Native: bash, read/write/edit, glob, grep
  │     ├── Subagent support
  │     └── Hooks for validation
  │
  └── MicrosoftGoalSeekingAgent ─── agent-framework
        ├── Thread state + GraphWorkflow
        ├── @function_tool decorator
        └── Middleware + telemetry

```

## PRs Required

### PR #2395 - Core (IN PROGRESS)

- [x] Eval harness L1-L12
- [x] Metacognition grader
- [x] Teaching session + NLG
- [x] Self-improvement error analyzer
- [x] Prompt templates
- [x] SDK abstraction layer (GoalSeekingAgent ABC)
- [ ] Final quality audit + exception handling
- [ ] Comprehensive 3-run eval

### PR B - Claude Agent SDK Implementation

- [ ] Issue + branch (DEFAULT_WORKFLOW steps 0-4)
- [ ] Design: map ClaudeAgent → GoalSeekingAgent (step 5)
- [ ] Implement: full claude-agents integration (steps 6-8)
- [ ] Test: unit tests + L1-L12 eval (steps 9-13)
- [ ] Quality audit + exception handling
- [ ] Self-improvement loop (eval → identify gaps → improve → re-eval)
- [ ] PR review + merge (steps 14-22)

### PR C - GitHub Copilot SDK Implementation (DEFAULT)

- Same workflow as PR B
- This becomes th

*[truncated — see source for full prompt]*