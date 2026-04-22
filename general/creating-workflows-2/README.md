# Creating Workflows

> This guide covers how to create your own Antfarm workflow.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Creating Custom Workflows

This guide covers how to create your own Antfarm workflow.

## Directory Structure

```
workflows/
└── my-workflow/
    ├── workflow.yml          # Workflow definition (required)
    └── agents/
        ├── agent-a/
        │   ├── AGENTS.md     # Agent instructions
        │   ├── SOUL.md       # Agent persona
        │   └── IDENTITY.md   # Agent identity
        └── agent-b/
            ├── AGENTS.md
            ├── SOUL.md
            └── IDENTITY.md
```

## workflow.yml

### Minimal Example

```yaml
id: my-workflow
name: My Workflow
version: 1
description: What this workflow does.

agents:
  - id: researcher
    name: Researcher
    role: analysis
    description: Researches the topic and gathers information.
    workspace:
      baseDir: agents/researcher
      files:
        AGENTS.md: agents/researcher/AGENTS.md
        SOUL.md: agents/researcher/SOUL.md
        IDENTITY.md: agents/researcher/IDENTITY.md

  - id: writer
    name: Writer
    role: coding
    description: Writes content based on research.
    workspace:
      baseDir: agents/writer
      files:
        AGENTS.md: agents/writer/AGENTS.md
        SOUL.md: agents/writer/SOUL.md
        IDENTITY.md: agents/writer/IDENTITY.md

steps:
  - id: research
    agent: researcher
    input: |
      Research the following topic:
      {{task}}

      Reply with:
      STATUS: done
      FINDINGS: what you found
    expects: "STATUS: done"

  - id: write
    agent: writer
    input: |
      Write content based on these findings:
      {{findings}}

      Original request: {{task}}

      Reply with:
      STATUS: done
      OUTPUT: the final content
    expects: "STATUS: done"
```

### Top-Level Fields

| Field | Required | Description |
|-------|----------|-------------|
| `id` | yes | Unique workflow identifier (lowercase, hyphens) |
| `name` | yes | Human-readable name |
| `version` | yes | Integer version number |
| `description` | yes | What the workflow does |
| `agents` | 

*[truncated — see source for full prompt]*