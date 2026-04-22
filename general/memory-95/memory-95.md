---
name: MEMORY
description: > Last Updated: 2026-03-01
> Review Cycle: Weekly

---

## Summary: Feb 24 - March 1, 2026 (Weekly Review)

### Big Wins This Week
1. **Neural-Memory 
model: claude-sonnet-4-5
---
# MEMORY.md - Vex's Long-Term Memory

> Last Updated: 2026-03-01
> Review Cycle: Weekly

---

## Summary: Feb 24 - March 1, 2026 (Weekly Review)

### Big Wins This Week
1. **Neural-Memory System Fully Operational** - Now using `nmem_context` at session start as primary memory
2. **3-Layer Research Workflow Established**:
   - Layer 1: `nmem_eternal` (forever project context)
   - Layer 2: `nmem_recap` (load eternal)
   - Layer 3: `papers.md` (file-based checklist)
3. **NullClaw Migration Project Started** - Discovered codebase already has sqlite.zig, mcp.zig, and full channel adapters
4. **Team Philosophy Cemented**: "If you want to go faster, go alone. If you want to go further, go together."

### Key Decisions Made
- Use **metadata (frontmatter)** for plan status tracking instead of relying on agent memory
- Deadline format for plans (more "creepy" 💀)
- Skip/postpone 12-hour AI course; focus on NullClaw code first

### What's Pruned/Outdated
- Old sub-agent setup experiments (Feb 28)
- Telegram pairing notes (Feb 27) - still valid but archived

---

## Daily Summary: Feb 28, 2026

### Morning Session
- Explored neural-memory MCP setup
- Tested mcporter with neural-memory tools
- Discovered `nmem_eternal` for permanent project storage

### Evening Session
- Discussed team philosophy: "go faster alone, go further together"
- Set up sub-agent workflow for OS class exercises

---

## Daily Summary: March 1, 2026

### Key Events
1. **Memory Workflow Evolution**:
   - Levia suggested using metadata for plans instead of internal memory
   - Updated Planner Agent rules with frontmatter format
   - Created `research/nullclaw-audit/papers.md` as checklist

2. **NullClaw Audit Started**:
   - Found NullClaw codebase in `~/nullclaw/`
   - Discovered `src/memory/engines/sqlite.zig` - potential for our neural-memory!
   - Created project in `plan/01-03-2026/nullclaw-migration/`

3. **3-Layer Research System Born**:
   - `nmem_eternal` → Save forever
   - `nmem_recap` → Load forever
   - `papers.md` → File checklist

### New Workflows Added to AGENTS.md
- Research workflow (3-layer system)
- Metadata format for planner tasks

---

## Active Projects

| Project | Status | Deadline |
|---------|--------|----------|
| NullClaw Migration (Audit Phase) | In Progress | 2026-03-07 |
| OS Class Exercises | Completed | - |

---

## Technical Notes

- **Memory System**: Primary = neural-memory (via mcporter), Secondary = file-based
- **Research**: Always use 3-layer system for codebase audits
- **Planning**: Always use frontmatter metadata in `plan/` folder
- **Tools**: mcporter is the bridge to neural-memory MCP

---

*Next Review: March 8, 2026 (Weekly)*