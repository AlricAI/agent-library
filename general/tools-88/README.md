# TOOLS

> > **Runs on Claude Sonnet** with file read/write, Bash, and Forge API.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# TOOLS.md — DirtSync Skills Enhancer (Code Scout)

> **Runs on Claude Sonnet** with file read/write, Bash, and Forge API.

## Available Tools
- **File read/write** — read agent instruction files, write lessons into them
- **Bash** — SSH to Mini for file edits, git commits, Drive access
- **Forge API** — read Framework Scout reports, Factory Analyst reports, post enhancement report
- **Grep** — search for patterns across agent instruction files

## Agent Instruction Files (on Mini)

```
/Users/dirtsyncmini/MCMForge/companies/dirtsync/agents/
├── ios-builder/
│   ├── AGENTS.md      ← Framework patterns, code conventions, common errors
│   ├── HEARTBEAT.md   ← Step-by-step build procedure, mandatory checks
│   ├── SOUL.md        ← Voice and principles (rarely update)
│   └── TOOLS.md       ← Available tools, API references, version info
├── test-runner/
│   ├── AGENTS.md      ← Test patterns, simulator commands, known issues
│   ├── HEARTBEAT.md   ← Test procedure, screenshot, email, Drive upload
│   └── TOOLS.md       ← Build commands, simulator commands, gws
├── critique-agent/
│   ├── AGENTS.md      ← Gold Star specs, color tables, measurement tolerances
│   ├── HEARTBEAT.md   ← Grading procedure, Drive tagging, verdict format
│   └── TOOLS.md       ← Spec locations, Forge API, Drive commands
├── qa-rider/
│   ├── AGENTS.md      ← QA patterns, test matrix, framework-specific checks
│   └── TOOLS.md       ← Test tools, xcodebuild, simctl
└── ship-engineer/
    ├── AGENTS.md      ← PR creation, rebase, code review checklist
    └── TOOLS.md       ← gh CLI, git commands
```

## Google Drive — QA Iterations

```bash
export PATH="/opt/homebrew/bin:/usr/local/bin:$PATH"
QA_FOLDER="1Vi2av_kjmCFDmV5dxgYwTQktfeUvgT1X"

# List issue folders
gws drive files list --params "q='${QA_FOLDER}' in parents and trashed=false" 2>&1 | grep -v "^Using keyring"

# List versions for an issue
ISSUE_FOLDER_ID="<from above>"
gws drive files list --params "q='${ISSUE_FOLDER_ID}' in parents an

*[truncated — see source for full prompt]*