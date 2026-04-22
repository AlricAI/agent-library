# AGENTS

> You are working inside the deft framework repository itself.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Deft — Development Framework (deft repo)

You are working inside the deft framework repository itself.
Full guidelines: main.md

## First Session (deft development)

**Headless bypass**: If you have been dispatched with a specific task (e.g. cloud agent, CI agent, scheduled run), skip the onboarding checks below and proceed directly to your task. The onboarding flow is for interactive sessions only.

Check what exists before doing anything else:

**USER.md missing** (~/.config/deft/USER.md or %APPDATA%\deft\USER.md):
→ Read skills/deft-setup/SKILL.md and start Phase 1 (user preferences)

**USER.md exists, PROJECT.md missing** (repo root):
→ Read skills/deft-setup/SKILL.md and start Phase 2 (project configuration)

**USER.md and PROJECT.md exist, SPECIFICATION.md missing** (repo root):
→ Read skills/deft-setup/SKILL.md and start Phase 3 (specification interview)

## Returning Sessions

When all config exists: read the guidelines, your USER.md preferences, and PROJECT.md, then continue with your task.

~ Run `skills/deft-sync/SKILL.md` to pull latest framework updates and validate project files.

### Deft Alignment Confirmation

! At the start of each interactive session, after loading AGENTS.md, confirm to the user that Deft Directive is active. The confirmation must be unambiguous -- for example: "Deft Directive active -- AGENTS.md loaded."

! If the agent detects a context window shift or is asked "are you using Deft?", re-confirm alignment by stating that Deft Directive is active and AGENTS.md was loaded.

⊗ Begin an interactive session without confirming Deft alignment to the user.

Note: A true UI indicator (e.g. Warp status bar) is deferred to Phase 5. This is a behavioral rule only.

## Skill Completion Gate

! When a skill's final step is complete, explicitly confirm skill exit and provide chaining instructions if applicable. The confirmation must be unambiguous -- for example: "{skill-name} complete -- exiting skill." followed by what the user/agent should

*[truncated — see source for full prompt]*