# Arch Skill Usage Guide

> This guide describes the live workflow surface for the repo.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# arch_skill Usage Guide

This guide describes the live workflow surface for the repo.

The current skill suite is:

- `arch-step`
- `miniarch-step`
- `arch-docs`
- `arch-mini-plan`
- `lilarch`
- `bugs-flow`
- `audit-loop`
- `comment-loop`
- `audit-loop-sim`
- `goal-loop`
- `north-star-investigation`
- `arch-flow`
- `arch-skills-guide`

Use `miniarch-step` for full-arch work when you want the trimmed command surface. Use `arch-step` when you need the broader or helper-heavy full-arch surface.

Other shipped skills:

- `arch-loop`
- `delay-poll`
- `wait`
- `agent-definition-auditor`
- `agents-md-authoring`
- `prompt-authoring`
- `skill-authoring`
- `amir-publish`
- `codex-review-yolo`
- `code-review`

Examples in this guide use Codex `$skill` notation. In Claude Code, invoke the same skill as `/skill`.

## Install

```bash
git clone git@github.com:aelaguiz/arch_skill.git
cd arch_skill
make install
```

For Codex automatic `auto-plan`, `implement-loop`, `arch-docs auto`, `audit-loop auto`, `comment-loop auto`, `audit-loop-sim auto`, `arch-loop`, `delay-poll`, and `wait`, also enable the Codex feature once:

```bash
codex features enable codex_hooks
```

Claude Code uses the installed settings-level `Stop` hook and does not depend on the Codex feature flag. Claude controllers that need fresh child review or check passes launch hook-suppressed child runs with `claude -p --settings '{"disableAllHooks":true}'`, so that child path must work with the machine's normal Claude auth.

For any supported auto controller in Codex or Claude Code, do not run the Stop hook yourself. After the controller is armed, just end the turn and let the installed Stop hook run.

Default local path:

- `~/.agents/skills/arch-step/`
- `~/.agents/skills/miniarch-step/`
- `~/.agents/skills/arch-docs/`
- `~/.agents/skills/arch-mini-plan/`
- `~/.agents/skills/lilarch/`
- `~/.agents/skills/bugs-flow/`
- `~/.agents/skills/audit-loop/`
- `~/.agents/skills/comment-loop/`
- `~/.agents/skills/audit-loop-si

*[truncated — see source for full prompt]*