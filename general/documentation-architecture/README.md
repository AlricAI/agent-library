# Documentation Architecture

> This document explains how documentation is organized in the Infrahub project to ensure consistency and discoverability.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Documentation Architecture

This document explains how documentation is organized in the Infrahub project to ensure consistency and discoverability.

## Principles

1. **Single Source of Truth**: All technical knowledge lives under `dev/`
2. **AGENTS.md as Gateway**: Component-level `AGENTS.md` files provide quick reference and point to `dev/` for details
3. **No Cross-References in Guidelines**: Individual guideline files don't link to each other; they link back to their index (README.md)
4. **Index-Based Navigation**: Each guideline category has a README.md that serves as the index and navigation hub

## File Structure

```
infrahub/
├── AGENTS.md                    # Root entry point, points to component AGENTS and dev/
├── backend/
│   └── AGENTS.md               # Backend overview, points to dev/guidelines/backend/
├── frontend/app/
│   └── AGENTS.md               # Frontend overview, points to dev/guidelines/frontend/
└── dev/
    ├── guidelines/              # How to write code
    │   ├── backend/
    │   │   └── python.md
    │   └── frontend/
    │       ├── README.md       # Index: lists all frontend guidelines
    │       ├── typescript.md   # Points back to README.md, not to other guidelines
    │       └── url-construction.md  # Points back to README.md, not to other guidelines
    ├── knowledge/               # How the system works
    ├── guides/                  # How to do specific tasks
    ├── adr/                     # Architecture decision records
    └── specs/                   # Feature specifications
```

## Documentation Flow

### For Agents/Developers Reading Documentation

1. **Start at component level**: `backend/AGENTS.md` or `frontend/app/AGENTS.md`
2. **Navigate to guidelines**: Follow link to `dev/guidelines/[backend|frontend]/`
3. **Use the index**: Start at `README.md` to see all available guidelines
4. **Read specific guidelines**: Each guideline is self-contained and focused

### For Agents/Developers Writing Documentation

##

*[truncated — see source for full prompt]*