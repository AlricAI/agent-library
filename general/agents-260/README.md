# AGENTS

> Repository-wide instructions for all agents working in this repo.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AGENTS.md

Repository-wide instructions for all agents working in this repo.

## Agent Loop

The **canonical builder / judge workflow** is in:

- `agent-loop/PROTOCOL.md`

If you are working on anything under `agent-loop/`, you MUST also read:

- this file (root `AGENTS.md`)
- `agent-loop/PROTOCOL.md`
- `agent-loop/ANTIPATTERNS.md`

### Builder / Judge Roles

- **{{BUILDER_AGENT_NAME}}** is the builder
- **{{JUDGE_AGENT_NAME}}** is the judge
- **{{COORDINATOR_NAME}}** is the coordinator and final decision-maker

{{JUDGE_AGENT_NAME}} must not drift into being the primary builder when acting as judge.

### File Ownership in Agent Loop

When operating inside `agent-loop/`:

- Do not edit `builder.md` if you are acting as judge
- Do not edit `judge.md` if you are acting as builder
- Preserve round history — rounds may only be moved to archive files via the Context Management process, never deleted or modified in place
- Update `status.json` when the protocol requires it

### Quick Reference

**Builder ({{BUILDER_AGENT_NAME}}):**
1. Read `task.md` for goal, scope, acceptance criteria
2. Read `judge.md` if it exists (previous round feedback)
3. Read **Phase Summaries** from both archive files (if they exist)
4. Perform context management checks (see PROTOCOL.md Context Management):
   - Phase compaction: if active file contains rounds from a prior phase, compact first
   - Round archival: if active file has 2+ rounds and you're writing round N >= 3, archive oldest
5. Append a new `## Round N — [phase]` section to `builder.md`
6. Update `status.json`: state → `ready_for_judge`
7. Do NOT edit `judge.md` or `judge-archive.md`

**Judge ({{JUDGE_AGENT_NAME}}):**
1. Read `task.md` for goal, scope, acceptance criteria
2. Read `builder.md` (latest round)
3. Review any changed artifacts referenced by the builder
4. Read **Phase Summaries** from both archive files (if they exist)
5. Perform context management checks (see PROTOCOL.md Context Management):
   - Phase compaction: if 

*[truncated — see source for full prompt]*