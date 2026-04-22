# WORKFLOW RUNTIME

> ## What It Is

Tandem's workflow automation runtime is the infrastructure layer that makes AI agents produce **verifiable, trustworthy artifacts** — n

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Tandem Workflow Automation Runtime

## What It Is

Tandem's workflow automation runtime is the infrastructure layer that makes AI agents produce **verifiable, trustworthy artifacts** — not just responses that sound plausible.

Most AI systems are evaluated on "does it sound good?" Tandem workflows are evaluated on:

- Did it produce the exact artifact it said it would?
- Does the artifact follow the exact contract it promised?
- Is every claim in the artifact backed by verifiable evidence?
- Can the system self-heal when something goes wrong, without losing context?

This is fundamentally harder to build than a chat interface. It's the difference between "AI that talks about work" and "AI that does work and can prove it."

## Why Existing AI Systems Fall Short

AI agents are confident even when wrong. They will confidently tell you they reviewed a file that doesn't exist, cite sources that weren't read, or claim a task is complete when the artifact is hollow.

Traditional guardrails try to solve this with prompts: "be careful," "cite your sources," "don't hallucinate." These work in demos and fall apart in production because:

1. **Prompts don't enforce behavior** — they guide it. The AI can still take credit for work it didn't do.
2. **Session state is ephemeral** — there's no persistent record of what was actually read vs. what was claimed.
3. **Retries are destructive** — when a run fails, context is lost. The next attempt has no memory of what went wrong.
4. **Validation is shallow** — checking that a file exists isn't the same as checking that the file's contents match what was promised.

## What Tandem's Runtime Does Differently

### 1. Artifact Contracts

Every workflow stage declares what it will produce and what evidence backs it. These aren't suggestions — they're enforced contracts.

When a research stage says "I reviewed files A, B, and C," Tandem validates:

- Did the session actually read A, B, and C?
- Are the paths concrete (not `*.yaml` or directo

*[truncated — see source for full prompt]*