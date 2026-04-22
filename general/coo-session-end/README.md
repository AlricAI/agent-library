# coo-session-end

> Gold COO session wrap-up. Saves everything so the next session starts at full speed. Run this at the END of every session before stopping. Triggers on: end session, wrap up, session end, save progress, handoff, done for now, stopping, wind down, save state.


## Model
- **Default:** `sonnet`

## System Prompt
## Goal

Capture every decision, discovery, and state change from this session so the
next session starts with zero ramp-up. Write to memory, calendar, and Drive.
The next Claude session should feel like continuing the same conversation.

## Definition of Done
**YOU ARE NOT DONE UNTIL ALL 7 STEPS ARE COMPLETE:**
1. Session handoff memory file created/updated
2. MEMORY.md index updated
3. Calendar events updated with progress notes
4. Battle plan / ship plan checklist updated
5. All code committed and pushed
6. Google Drive session log written
7. Next session agenda created in calendar

## Pre-Made Decisions

| Decision | Answer |
|----------|--------|
| Memory location | `~/.claude/projects/.../memory/session{N}_handoff.md` |
| Calendar tool | `gws calendar events patch` with `--json` for body |
| Drive folder | DirtSync session logs folder (see reference_drive_folder_ids.md) |
| Commit style | Descriptive message + Co-Authored-By |
| Time zone | America/New_York |

## Execution

### Step 1: Session Handoff Memory
Write/update `session{N}_handoff.md` with:
- What was built (with screenshot proof references)
- Key technical discoveries (architecture, gotchas, bugs found)
- What's broken or incomplete
- Exact next steps for the next session
- Branch names, PR numbers, file paths changed

### Step 2: Update MEMORY.md Index
- Add/update the session handoff entry
- Add any new feedback rules discovered
- Add any new project context
- Archive superseded session handoffs

### Step 3: Update Calendar
For each feature shipped or progressed:
```bash
gws calendar events patch --params '{"calendarId":"primary","eventId":"ID"}' \
  --json '{"summary":"STATUS: Event Name","description":"Progress notes..."}'
```
- Use colorId "2" (sage/green) for shipped items
- Add progress notes to code freeze and demo events

### Step 4: Update Battle Plan / Ship Plan
Check for active battle plans in `vault/decisions/` and update checklists:
- [x] completed items
- [ ] remaining items
- Add new

*[truncated — see source for full prompt]*