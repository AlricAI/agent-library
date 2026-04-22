# TANDEM CLI VISION

> You are implementing a Rust TUI using ratatui + crossterm for tandem-cli.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
You are implementing a Rust TUI using ratatui + crossterm for tandem-cli.

REFERENCE (CURRENT UI MUST BE PRESERVED)
The current UI elements must remain visible and recognizable:

- Top-left: “New session”
- Top-right: green dot + “Online” (or Offline)
- Main transcript area shows “you:” + messages
- Input box labeled “Input” with placeholder:
  “Type prompt or /command... (Tab for autocomplete)”
- Bottom status strip ALWAYS visible showing selected:
  MODE | PROVIDER | MODEL | SESSION/ENGINE ID
  Example: “Ask | openrouter | z-ai/glm-5 | dcad20d4”
  Do NOT remove/replace these indicators. You may add an “Active: Agent X” segment, but keep the core strip.

PRIMARY GOAL
Make it feel like a developer CLI (opencode-cli / codex-cli / gemini-cli / claude-cli):

- One canonical transcript per agent
- Smooth streaming output
- Keyboard-first navigation
- Commands + palette later, but core interaction must be clean

NEW FEATURE GOAL: MULTI-AGENT IN ONE WINDOW (NO OS WINDOWS REQUIRED)
Support running multiple agents concurrently via event streams WITHOUT interleaving their tokens into one transcript.
Users can either:
A) Focus a single agent (default)
B) Toggle a GRID view (2–4 panes) showing multiple agents at once

IMPORTANT UX PRINCIPLES

- Never stream multiple agents into the same transcript at the same time.
- In Focus mode, only the active agent’s transcript + streaming row is shown.
- Other agents can show summarized “activity” badges/lines (optional), but not full token spam.
- In Grid mode, each pane shows that agent’s transcript (trimmed/scrollable) and optionally its streaming row inside the pane.

UI MODES

1. FOCUS MODE (default)
   ┌─ New session ────────────────────────────────────────────────● Online ───────┐
   │ MAIN VIEWPORT (scroll): Active agent transcript + tool events + streaming │
   ├─ Input ─────────────────────────────────────────────────────────────────────┤
   │ > composer (active agent) │
   ├─────────────────────────────────────────────────────

*[truncated — see source for full prompt]*