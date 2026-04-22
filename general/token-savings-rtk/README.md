# Token Savings Rtk

> Common dev commands return tokens that are mostly noise — git status icons, npm dependency trees, `gh pr view` headers.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Token Savings with an Output-Compaction Proxy

Common dev commands return tokens that are mostly noise — git status icons, npm dependency trees, `gh pr view` headers. A single `git status` on a moderate repo can burn 5–10K tokens; a `git log -20` can hit 15K. Across a multi-hour session, this dominates context spend.

> _Pattern based on `rtk` (Rust Token Killer), an open-source CLI proxy that wraps common dev tools and returns AI-friendly compact output. The technique is general — any wrapper or filter that strips visual noise while preserving semantic content captures most of the savings._

## When to use

**Use a compaction proxy when**:
- An AI session burns >30% of context on tool output (check via `rtk discover` or your assistant's metrics).
- The same commands recur many times per session (`git status`, `git diff`, `git log`, `gh pr view`, `npm ls`, `docker ps`, `ls -la`).
- The full output isn't useful for reasoning — only the structured fields matter.

**Do not use** when:
- Raw output is being parsed by another tool (the wrapper may strip chars another parser needs).
- Debugging the wrapper itself.
- Streaming output is required (most wrappers buffer).

## Wire it up transparently

For Claude Code, register a `PreToolUse` hook with matcher `Bash` that calls a rewriter script. The rewriter receives the JSON tool input, asks the proxy whether the command has a compact equivalent, and returns an `updatedInput` with the rewritten command + `permissionDecision: allow`. The user types `git status`; Claude executes `rtk git status`. No friction.

For Codex / opencode (no PreToolUse hook), document the prefix in `AGENTS.md` so the model learns to prefix manually. Less reliable but better than nothing.

## Verify it's working

A surprisingly common failure mode: the hook script exists at the right path but isn't registered in `settings.json`. Sanity check:

```bash
echo '{"tool_input":{"command":"git status"}}' | bash ~/.claude/hooks/rtk-rewrite.sh
# Expect: {"ho

*[truncated — see source for full prompt]*