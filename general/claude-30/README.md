# CLAUDE

> - Repo: https://github.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Repository Guidelines

- Repo: https://github.com/openclaw/openclaw
- In chat replies, file references must be repo-root relative only (example: `extensions/bluebubbles/src/channel.ts:80`); never absolute paths or `~/...`.
- GitHub issues/comments/PR comments: use literal multiline strings or `-F - <<'EOF'` (or $'...') for real newlines; never embed "\\n".
- GitHub comment footgun: never use `gh issue/pr comment -b "..."` when body contains backticks or shell chars. Always use single-quoted heredoc (`-F - <<'EOF'`) so no command substitution/escaping corruption.
- GitHub linking footgun: don’t wrap issue/PR refs like `#24643` in backticks when you want auto-linking. Use plain `#24643` (optionally add full URL).
- PR landing comments: always make commit SHAs clickable with full commit links (both landed SHA + source SHA when present).
- PR review conversations: if a bot leaves review conversations on your PR, address them and resolve those conversations yourself once fixed. Leave a conversation unresolved only when reviewer or maintainer judgment is still needed; do not leave bot-conversation cleanup to maintainers.
- GitHub searching footgun: don't limit yourself to the first 500 issues or PRs when wanting to search all. Unless you're supposed to look at the most recent, keep going until you've reached the last page in the search
- Security advisory analysis: before triage/severity decisions, read `SECURITY.md` to align with OpenClaw's trust model and design boundaries.

## Auto-close labels (issues and PRs)

- If an issue/PR matches one of the reasons below, apply the label and let `.github/workflows/auto-response.yml` handle comment/close/lock.
- Do not manually close + manually comment for these reasons.
- Why: keeps wording consistent, preserves automation behavior (`state_reason`, locking), and keeps triage/reporting searchable by label.
- `r:*` labels can be used on both issues and PRs.

- `r: skill`: close with guidance to publish skills on Clawhub.
- `r: s

*[truncated — see source for full prompt]*