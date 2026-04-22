# TOOLS

> Reference: scoring rubric details, schedule generation, state schemas.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# TOOLS.md — Prompt Auditor

Reference: scoring rubric details, schedule generation, state schemas.

---

## Scoring Rubric — 10 Axes Detailed

### Axis 1: Identity clarity (1-10)
- **10:** First paragraph states what the agent IS and what it is NOT, in one sentence each
- **7:** States what the agent IS
- **4:** Generic intro ("You are the X agent for Y")
- **1:** No identity statement at all

### Axis 2: Frontmatter completeness (1-10)
Required fields: `name`, `title`, `reportsTo`, `company`, `companyId`, `skills`
- **10:** All fields present + valid UUID format for companyId
- **7:** Missing 1 optional field
- **4:** No frontmatter at all (plain markdown header instead)
- **1:** File missing

### Axis 3: Skills wiring (1-10)
- **10:** `skills:` contains `forge` + `lessons-learned-loop` + any domain skills
- **7:** `skills:` present but missing `lessons-learned-loop`
- **4:** `skills: []` empty
- **1:** No skills field

### Axis 4: Measurable acceptance (1-10)
Count vague vs specific language in the Rules section:
- **10:** 90%+ of rules include a number, file path, or exact string
- **7:** 60%+ specific
- **4:** Mostly vague ("be careful", "improve quality", "try to avoid")
- **1:** All vague

### Axis 5: Definition of Done (1-10)
- **10:** Explicit "YOU ARE NOT DONE UNTIL" block with 5+ numbered criteria
- **7:** "Done when" list but less than 5 criteria
- **4:** Implicit (buried in prose)
- **1:** Missing entirely

### Axis 6: Pre-Made Decisions (1-10)
- **10:** Dedicated table with 5+ settled decisions
- **7:** Table exists but fewer than 5 rows
- **4:** Decisions scattered in prose
- **1:** No pre-made decisions documented

### Axis 7: Gotchas section (1-10)
- **10:** Table format with 5+ entries, each with Issue | Solution columns
- **7:** 3-4 gotchas in any format
- **4:** 1-2 gotchas
- **1:** No gotchas section

### Axis 8: Output format (1-10)
- **10:** Template showing exact markdown/JSON structure of what the agent produces
- **7:** Prose description of

*[truncated — see source for full prompt]*