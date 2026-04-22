# New Scenarios 2026 04

> Ten repo-grounded candidate scenarios to add after the current seed suite.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# QA Scenario Expansion - Round 2

Ten repo-grounded candidate scenarios to add after the current seed suite.

## 1. On-demand memory tools in channel context

- Goal: verify the agent uses `memory_search` plus `memory_get` instead of bluffing when a channel message asks about prior notes.
- Flow:
  - Seed `MEMORY.md` or `memory/*.md` with a fact not present in the current transcript.
  - Ask in a channel thread for that fact.
  - Verify tool usage and final answer accuracy.
- Pass:
  - `memory_search` runs first.
  - `memory_get` narrows to the right lines.
  - Final answer cites the remembered fact correctly without cross-session leakage.
- Docs: `docs/concepts/memory.md`, `docs/concepts/memory-search.md`
- Code: `extensions/memory-core/src/tools.ts`, `extensions/memory-core/src/prompt-section.ts`

## 2. Memory failure fallback

- Goal: verify memory failure is graceful when embeddings/search are unavailable.
- Flow:
  - Disable or break the embedding-backed memory path.
  - Ask for prior-note recall.
  - Verify the agent surfaces uncertainty and next action instead of hallucinating.
- Pass:
  - Tool failure does not crash the run.
  - Agent says it checked and could not confirm.
  - Report includes the remediation hint.
- Docs: `docs/concepts/memory.md`, `docs/help/faq.md`
- Code: `extensions/memory-core/src/tools.shared.ts`, `extensions/memory-core/src/tools.citations.test.ts`

## 3. Model switch with tool continuity

- Goal: verify model switching preserves session context and tool availability, not just plain text continuity.
- Flow:
  - Start on one model.
  - Switch to another configured model.
  - Ask for a tool-using follow-up such as file read or memory lookup.
- Pass:
  - Switch is reflected in runtime state.
  - Tool call still succeeds after the switch.
  - Final answer keeps prior context.
- Docs: `docs/help/testing.md`, `docs/concepts/model-failover.md`
- Code: `extensions/qa-lab/src/suite.ts`, `docs/web/webchat.md`

## 4. MCP-backed recall via QMD/m

*[truncated — see source for full prompt]*