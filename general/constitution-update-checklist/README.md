# Constitution Update Checklist

> When amending the constitution (`/memory/constitution.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Constitution Update Checklist

When amending the constitution (`/memory/constitution.md`), ensure all dependent documents are updated to maintain consistency.

## Templates to Update

### When adding/modifying ANY article:
- [ ] `/templates/plan-template.md` - Update Constitution Check section
- [ ] `/templates/spec-template.md` - Update if requirements/scope affected
- [ ] `/templates/tasks-template.md` - Update if new task types needed
- [ ] `/.claude/commands/plan.md` - Update if planning process changes
- [ ] `/.claude/commands/tasks.md` - Update if task generation affected
- [ ] `/CLAUDE.md` - Update runtime development guidelines

### Article-specific updates:

#### Article I (Library-First):
- [ ] Ensure templates emphasize library creation
- [ ] Update CLI command examples
- [ ] Add llms.txt documentation requirements

#### Article II (CLI Interface):
- [ ] Update CLI flag requirements in templates
- [ ] Add text I/O protocol reminders

#### Article III (Test-First):
- [ ] Update test order in all templates
- [ ] Emphasize TDD requirements
- [ ] Add test approval gates

#### Article IV (Integration Testing):
- [ ] List integration test triggers
- [ ] Update test type priorities
- [ ] Add real dependency requirements

#### Article V (Observability):
- [ ] Add logging requirements to templates
- [ ] Include multi-tier log streaming
- [ ] Update performance monitoring sections

#### Article VI (Versioning):
- [ ] Add version increment reminders
- [ ] Include breaking change procedures
- [ ] Update migration requirements

#### Article VII (Simplicity):
- [ ] Update project count limits
- [ ] Add pattern prohibition examples
- [ ] Include YAGNI reminders

## Validation Steps

1. **Before committing constitution changes:**
   - [ ] All templates reference new requirements
   - [ ] Examples updated to match new rules
   - [ ] No contradictions between documents

2. **After updating templates:**
   - [ ] Run through a sample implementation plan
   - [ ] Verify all

*[truncated — see source for full prompt]*