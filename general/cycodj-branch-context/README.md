# Cycodj Branch Context

> ## The Pain 😫

**Current State:**
The `branches` command shows me the tree structure beautifully:

```
📁 08:27 - Chat History Journal Tool
  ├─ 08:5

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# TODO: cycodj - Branch Context (Why Did This Branch?)

## The Pain 😫

**Current State:**
The `branches` command shows me the tree structure beautifully:

```
📁 08:27 - Chat History Journal Tool
  ├─ 08:56 - Chat History Journal Tool
  ├─ 09:10 - Chat History Journal Tool
  ├─ 09:22 - Chat History Journal Tool
  └─ 09:34 - Chat History Journal Tool
```

**But I can't tell WHY they branched!**

All I see is:
- Timestamp
- Title (often same for branches)
- That it branched

**The Problems:**
- **Branches look identical:** "Chat History Journal Tool" repeated 5 times - which is which?
- **No context:** Why did I branch at 08:56? What was I trying differently?
- **Have to investigate:** Must open each conversation to understand
- **Pattern invisible:** Can't see "Phase 0 → Phase 1 → Phase 2" progression
- **Story lost:** The branching tells a story but I can't read it

**Real-world frustration:**
Today analyzing your weekend, I saw:
```
📁 09:45 - CDR Project Restart Instructions
  ├─ 09:46 - CDR Project Restart Instructions (iteration 1)
    ├─ 09:58 - CDR Project Restart Instructions (iteration 2)
      ├─ 10:01 - CDR Project Restart Instructions (iteration 3)
```

12 branches deep! But WHY? What changed each time?

I had to:
1. Note the conversation IDs
2. Use `show` on each one
3. Read the first user message
4. Manually reconstruct the story

**It took 15 minutes to understand a tree that should explain itself.**

---

## The Cure 💊

**What I Want:**
Show me WHY each branch exists - give me context:

```bash
cycodj branches --date 2025-12-20 --with-context
```

**Output:**
```
📁 08:27 - Chat History Journal Tool (73 msgs)
   > "can you make a new worktree for cycodj..."
   
  ├─ 08:56 - Phase 0: Setup (79 msgs)
  │  > "research cycodgr first..."
  │  Branched: Added research phase
  │
  ├─ 09:10 - Phase 1: Implementation (161 msgs)
  │  > "now implement the list command..."
  │  Branched: Starting implementation
  │
  ├─ 09:22 - Phase 2: Search Feature (152 msgs

*[truncated — see source for full prompt]*