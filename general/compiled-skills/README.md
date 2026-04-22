# Compiled Skills

> JIT compilation for UI automation.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Compiled Skills

JIT compilation for UI automation. A compiled skill eliminates all OCR calls by capturing coordinates, timing, and scroll sequences during a learning run. The compiled file is fully self-contained — executable without AI or OCR, pure input injection plus timing. Like compiling source to machine code. Compilation works with both YAML and SKILL.md skill formats.

## The Problem

Each OCR-dependent step costs ~500ms (screencapture + Vision OCR). A 10-step skill touching `tap`, `wait_for`, `scroll_to`, and `assert_visible` makes 10+ OCR calls — that's 5+ seconds of OCR overhead alone, on top of actual UI interaction time.

For regression suites running dozens of skills, OCR dominates the total runtime. Worse, OCR introduces non-determinism: text recognition confidence varies between runs, and fuzzy matching can find the wrong element if the screen layout shifts slightly.

## The Solution: Compile Once, Replay Forever

Run the skill once against a real device. The compiler observes everything — which element matched, at what coordinates, with what confidence, how long each `wait_for` took, how many scrolls `scroll_to` needed. It saves all of this into a `.compiled.json` file alongside the source skill file.

On subsequent runs, the test runner detects the compiled file and replays the skill using cached data — zero OCR, zero AI, zero non-determinism.

```
Source:     apps/settings/check-about.md (or .yaml)
Compiled:   apps/settings/check-about.compiled.json
```

## How It Works

There are two ways to compile a skill: AI-driven compilation (recommended) and CLI compilation. Both produce identical `.compiled.json` files.

### AI-Driven Compilation (Recommended)

When an AI agent executes a skill via MCP tools, it already has all the data needed for compilation — tap coordinates from `describe_screen`, timing from step execution, scroll counts from `scroll_to`. Two MCP tools let the AI report this data back to the server:

1. **`record_step`** — called af

*[truncated — see source for full prompt]*