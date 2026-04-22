# Codex Creative Routing 2026 04 16

> Date: 2026-04-16

Status: Active

Scope: Routing policy for image-heavy brand, marketing, and frontend work across Codex, Hermes, and server-side auto

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Codex Creative Routing

Date: 2026-04-16

Status: Active

Scope: Routing policy for image-heavy brand, marketing, and frontend work across Codex, Hermes, and server-side autonomous workers in `Blueprint-WebApp`.

Source note:
- OpenAI, "Codex for (almost) everything," published April 16, 2026:
  Codex can use `gpt-image-1.5` to generate and iterate on images inside the same workflow as screenshots and code.

## Decision

Blueprint will treat Codex-native image generation via Codex desktop OAuth as the default image lane only for work that is actually executed inside Codex.

Blueprint will not assume that Hermes-backed agents or server-side autonomous workers inherit Codex image capability.

## Operating Rule

- Codex brand/marketing/frontend agents: use Codex-native image generation by default.
- Hermes agents: do not assume image generation capability.
- Server-side autonomous workers: do not call a separate paid image API for final image execution.
- Video generation remains on the explicit provider path. Current default: OpenRouter video.

## Why

- The new Codex image capability is attached to Codex execution, not to every Paperclip lane generically.
- Most Blueprint growth and research agents are Hermes-backed and should continue to own planning, copy, evidence gathering, and routing rather than final image execution.
- The current scheduled creative factory and admin creative routes are server-side workflows and should prepare proof-led prompt packs, then hand final image execution to Codex instead of calling a separate image API.

## Audited Agent Set

The following agents should follow the new Codex image-routing rule.

### Execute Image Work In Codex

These lanes should use Codex-native image generation by default when the assigned work needs generated imagery, mockups, design explorations, or asset iteration.

| Agent | Current runtime role | Policy |
|---|---|---|
| `webapp-codex` | Codex implementation lane for `Blueprint-WebApp` | Default execution la

*[truncated — see source for full prompt]*