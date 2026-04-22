# Other Platforms

> How to load your Context Stack into additional AI coding tools and platforms.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Other Platforms

How to load your Context Stack into additional AI coding tools and platforms.

Most AI coding tools follow a common pattern: read a markdown file from the project root or a user-level config directory. The file name varies by tool. The content format is the same: plain markdown with your context components.


## GitHub Copilot

**Context file:** `.github/copilot-instructions.md` in the repository root.

Copilot reads this file for project-level coding context and guidelines.

```
<project-root>/
└── .github/
    └── copilot-instructions.md
```

**What to include:**

```markdown
# Project Context

## Values and Boundaries
[Key points from values-and-boundaries.md]

## Domain Map
[Relevant sections from domain-map.md]

## Tool Ecosystem
[Relevant sections from tool-ecosystem.md]

## Communication DNA
[Key patterns from communication-dna.md]
```

Copilot's instructions work best when focused on coding patterns, naming conventions, and project-specific technical context. Identity and communication style components have less impact here since Copilot primarily generates code, not prose.


## Windsurf

**Context file:** `.windsurfrules` in the project root.

```
<project-root>/
└── .windsurfrules
```

**What to include:**

```markdown
# Project Context

## Professional Identity
[Paste professional-identity.md content]

## Communication DNA
[Paste communication-dna.md content]

## Domain Map
[Paste domain-map.md and tool-ecosystem.md content]

## Strategic Context
[Paste strategic-context.md content]
```

Windsurf supports rich context, so include both your identity/style components and project-specific substance.


## Microsoft Copilot

Microsoft Copilot comes in two versions with different capabilities. Identify which version you have before proceeding.

- **Microsoft 365 Copilot (Enterprise)**: Supports persistent agents via Copilot Studio. You can create discovery agents and context-loading agents.
- **Copilot in Edge / copilot.microsoft.com (Consume

*[truncated — see source for full prompt]*