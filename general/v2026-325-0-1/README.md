# V2026.325.0

> > Released: 2026-03-25

## Highlights

- **Company import/export** — Full company portability with a file-browser UX for importing and exporting agent

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# v2026.325.0

> Released: 2026-03-25

## Highlights

- **Company import/export** — Full company portability with a file-browser UX for importing and exporting agent companies. Includes rich frontmatter preview, nested file picker, merge-history support, GitHub shorthand refs, and CLI `company import`/`company export` commands. Imported companies open automatically after import, and heartbeat timers are disabled for imported agents by default. ([#840](https://github.com/paperclipai/paperclip/pull/840), [#1631](https://github.com/paperclipai/paperclip/pull/1631), [#1632](https://github.com/paperclipai/paperclip/pull/1632), [#1655](https://github.com/paperclipai/paperclip/pull/1655))
- **Company skills library** — New company-scoped skills system with a skills UI, agent skill sync across all local adapters (Claude, Codex, Pi, Gemini), pinned GitHub skills with update checks, and built-in skill support. ([#1346](https://github.com/paperclipai/paperclip/pull/1346))
- **Routines and recurring tasks** — Full routines engine with triggers, routine runs, coalescing, and recurring task portability. Includes API documentation and routine export support. ([#1351](https://github.com/paperclipai/paperclip/pull/1351), [#1622](https://github.com/paperclipai/paperclip/pull/1622), @aronprins)

## Improvements

- **Inline join requests in inbox** — Join requests now render inline in the inbox alongside approvals and other work items.
- **Onboarding seeding** — New projects and issues are seeded with goal context during onboarding for a better first-run experience.
- **Agent instructions recovery** — Managed agent instructions are recovered from disk on startup; instructions are preserved across adapter switches.
- **Heartbeats settings page** — Shows all agents regardless of interval config; added a "Disable All" button for quick bulk control.
- **Agent history via participation** — Agent issue history now uses participation records instead of direct assignment lookups.
- **Alphabeti

*[truncated — see source for full prompt]*