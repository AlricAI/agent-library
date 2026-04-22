# V0.3.1

> > Released: 2026-03-12

## Highlights

- **Gemini CLI adapter** — Full local adapter support for Google's Gemini CLI. Includes API-key detection, turn

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# v0.3.1

> Released: 2026-03-12

## Highlights

- **Gemini CLI adapter** — Full local adapter support for Google's Gemini CLI. Includes API-key detection, turn-limit handling, sandbox and approval modes, skill injection into `~/.gemini/`, and yolo-mode default. ([#452](https://github.com/paperclipai/paperclip/pull/452), [#656](https://github.com/paperclipai/paperclip/pull/656), @aaaaron)
- **Run transcript polish** — Run transcripts render markdown, fold command stdout, redact home paths and user identities, and display humanized event labels across both detail and live surfaces. ([#648](https://github.com/paperclipai/paperclip/pull/648), [#695](https://github.com/paperclipai/paperclip/pull/695))
- **Inbox refinements** — Improved tab behavior, badge counts aligned with visible unread items, better mobile layout, and smoother new-issue submit state. ([#613](https://github.com/paperclipai/paperclip/pull/613))
- **Improved onboarding wizard** — Onboarding now shows Claude Code and Codex as recommended adapters, collapses other types, and features animated step transitions with clickable tabs. Adapter environment checks animate on success and show debug output only on failure. ([#700](https://github.com/paperclipai/paperclip/pull/700))

## Improvements

- **Instance heartbeat settings sidebar** — View and manage heartbeat configuration directly from the instance settings page with compact grouped run lists. ([#697](https://github.com/paperclipai/paperclip/pull/697))
- **Project and agent configuration tabs** — New tabbed configuration UI for projects and agents, including execution workspace policy settings. ([#613](https://github.com/paperclipai/paperclip/pull/613))
- **Agent runs tab** — Agent detail pages now include a dedicated runs tab.
- **Configurable attachment content types** — The `PAPERCLIP_ALLOWED_ATTACHMENT_TYPES` env var lets operators control which file types can be uploaded. ([#495](https://github.com/paperclipai/paperclip/pull/495), @subhendukundu)
- 

*[truncated — see source for full prompt]*