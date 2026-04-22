# Commands

> Workflows for scoped changes to an existing codebase — propose, implement, verify, archive.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Change Lifecycle Commands

Workflows for scoped changes to an existing codebase — propose, implement, verify, archive.

Legend (from RFC2119): !=MUST, ~=SHOULD, ≉=SHOULD NOT, ⊗=MUST NOT, ?=MAY.

**⚠️ See also**: [verification/verification.md](./verification/verification.md) | [resilience/continue-here.md](./resilience/continue-here.md) | [vbrief/vbrief.md](./vbrief/vbrief.md)

---

## Overview

Each change is a self-contained unit of work with its own folder in `history/changes/`. The lifecycle is:

```
/deft:change <name>  →  /deft:change:apply  →  /deft:change:verify  →  /deft:change:archive
        │                          │                          │                          │
   Create proposal          Implement tasks           Verify outcomes          Move to archive
```

---

## `/deft:change <name>`

Create a scoped change proposal.

### Process

- ! Create `history/changes/<name>/` with the artifacts below
- ! Read existing specs in the project (if any) to understand current state
- ~ Run `/deft:run:discuss` first if the change has gray areas
- ~ Run `/deft:run:research` first if the domain is unfamiliar

### Artifacts

```
history/changes/<name>/
├── proposal.md          ← Why this change, what's affected, scope
├── design.md            ← Technical approach, alternatives considered
├── tasks.vbrief.json    ← Implementation tasks in vBRIEF format
└── specs/               ← Spec deltas (how requirements change)
    └── <capability>/
        └── spec.md      ← New or modified requirements
```

### proposal.md

- ! **Problem** — what's wrong or missing
- ! **Change** — what this proposal does about it
- ! **Scope** — what's in, what's explicitly out
- ~ **Impact** — what existing code/specs are affected
- ~ **Risks** — what could go wrong

### design.md

- ! **Approach** — how to implement the change
- ~ **Alternatives** — what else was considered and why not
- ~ **Dependencies** — what must exist before this works
- ? Skip if the change is trivial (< 1 h

*[truncated — see source for full prompt]*