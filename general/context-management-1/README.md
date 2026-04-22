# Context Management

> > Token waste is the silent tax on every AI-assisted session.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Context Management for AI Coding

> Token waste is the silent tax on every AI-assisted session. Manage it actively.

## Token Optimization

### Progressive Loading
Don't read entire files upfront. Build context incrementally:
1. Start with project structure (glob, ls)
2. Read specific functions (grep for signatures, then read targeted lines)
3. Load full files only when editing them

### Context Hygiene
- Clean context between unrelated tasks (`/compact`, `/clear`, or start a new session)
- Reference files by path (`@filename`) instead of pasting contents into chat
- Run `/compact` at **60-70%** context usage — waiting until 90% risks hitting session limits
- Break long sessions into focused segments — a 500-message session is slower than 5 fresh ones

### MEMORY.md Discipline
The `MEMORY.md` index is loaded into context on **every message**. Bloat here is a fixed cost — it never goes away during the session.

- Hard limit: **200 lines** (entries after line 200 are silently truncated)
- Keep each entry to one line under ~150 characters
- Move details into topic files (architecture.md, gotchas.md, workflows.md)
- Only put information in MEMORY.md that you need to find *other* files
- Audit and trim periodically — the index is a pointer, not storage

### MCP Server Strategy
- Keep < 10 servers active globally
- Prefer remote/lazy servers over local ones — remote tools register on-demand (cheaper on context)
- Enable specialized servers per-project, not globally
- Heavy servers (Playwright, Stitch, HuggingFace) should be disabled by default
- **Plugin dual-registration**: Claude Code plugins can register the same MCP server a second time under a `mcp__plugin_*` namespace. If a server is in `.mcp.json` AND enabled as a plugin, every tool appears twice. Audit with `claude plugin list` and disable the plugin version for servers you manage directly.
- **`CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1`**: Triples all MCP tool entries by adding a third `mcp__agents__*` namespace. 

*[truncated — see source for full prompt]*