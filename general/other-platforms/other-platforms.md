---
name: Other Platforms
description: How to load your Context Stack into additional AI coding tools and platforms.
model: claude-sonnet-4-5
---
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
- **Copilot in Edge / copilot.microsoft.com (Consumer)**: Does not support persistent agents. Use Option A (paste the discovery prompt into a conversation).

### Build Your Context Stack

**Enterprise (Copilot Studio):**

Create a reusable discovery agent:

1. Open **Copilot Studio** (copilotstudio.microsoft.com)
2. Create a new agent named "Context Discovery"
3. Paste the prompt block from `discovery/quick-start.md` or `discovery/context-discovery-session.md` into the **Instructions** field
4. Start a conversation with the agent and answer the questions
5. Save the drafted context-component files as `.md` files

For detailed agent configuration, enterprise considerations, and prompting best practices, see `guides/discovery-agents.md`.

**Consumer (Copilot in Edge / copilot.microsoft.com):**

Paste the discovery prompt directly into a new conversation. Save the prompt as a text snippet for reuse. See `discovery/quick-start.md` for the prompt.

### Microsoft 365 Copilot (Enterprise)

Once you have your context files, create a declarative agent for daily use:

1. Open **Copilot Studio** (copilotstudio.microsoft.com)
2. Create a new agent or edit an existing one
3. Add your context to the **Instructions** field

**What to include:**

```markdown
# Professional Context

## Professional Identity
[Paste professional-identity.md content]

## Communication DNA
[Paste communication-dna.md content]

## Strategic Context
[Paste strategic-context.md content]

## Domain Map
[Paste relevant domain-map.md sections]
```

### Copilot in Edge / copilot.microsoft.com

For the consumer version of Copilot, there is no persistent custom instructions feature equivalent to ChatGPT's Custom Instructions. Paste your context at the start of each conversation, or use a text expander to insert it quickly.

**Recommended approach:**

Save a condensed version of your professional-identity and communication-dna as a text snippet. Paste it as the first message in any Copilot conversation where you need personalized output.


## OpenCode

**Context file:** `AGENTS.md` in the project root.

OpenCode follows the same pattern as Codex. See the [Codex guide](codex.md) for detailed setup instructions. The file format and content recommendations are identical.

```
<project-root>/
└── AGENTS.md
```


## Aider

**Configuration:** `.aider.conf.yml` in the project root, plus read-only context files via command-line flag.

### Option 1: Read Flag

Create a file with your context and load it when launching Aider using the `--read` flag, which adds files as read-only context:

```bash
aider --read .aider-context.md
```

**File:** `<project-root>/.aider-context.md`

```markdown
# My Context

## Professional Identity
[Paste professional-identity.md content]

## Communication DNA
[Paste communication-dna.md content]

## Values and Boundaries
[Paste values-and-boundaries.md content]
```

### Option 2: Configuration File

Add the read file to your Aider config so it loads automatically:

**File:** `<project-root>/.aider.conf.yml`

```yaml
read: .aider-context.md
```

This loads your context automatically without the command-line flag.


## Cline

**Context file:** `.clinerules` in the project root.

```
<project-root>/
└── .clinerules
```

**What to include:**

```markdown
# Project Context

## Professional Identity
[Paste professional-identity.md content]

## Operating Rhythm
[Paste communication-dna.md and operating-rhythm.md content]

## Domain Map
[Paste domain-map.md content]

## Values and Boundaries
[Paste values-and-boundaries.md content]

## Strategic Context
[Paste strategic-context.md content]
```

Cline reads `.clinerules` at session start and applies it throughout the conversation.


## Continue.dev

**Configuration:** `.continue/config.json` in the project root or `~/.continue/config.json` for global settings.

### System Message

Add your context as a system message in the config:

**File:** `<project-root>/.continue/config.json`

```json
{
  "systemMessage": "You are working with a senior professional. Here is their context:\n\n## Professional Identity\n[professional-identity.md content]\n\n## Communication DNA\n[communication-dna.md content]\n\n## Domain Map\n[domain-map.md content]"
}
```

### Limitations

The system message must be a single JSON string. For longer context, keep it concise or use escape characters for newlines. This is less ergonomic than markdown file approaches.

### Alternative: .continuerules

Continue also supports `.continuerules` files in the project root, which accept markdown format:

```
<project-root>/
└── .continuerules
```

Check Continue's current documentation for the latest supported file conventions.


## The Universal Pattern

If you encounter a new AI coding tool not listed here, look for one of these patterns:

1. **Named markdown file in project root.** Check the tool's docs for the expected filename. Common names: `AGENTS.md`, `.rules`, `.<toolname>rules`, `<TOOLNAME>.md`.

2. **Config directory with rules files.** Look for a `.<toolname>/rules/` directory, either at the project root or in your home directory.

3. **System prompt in config.** Check for a `config.json`, `config.yaml`, or similar file that accepts a `systemMessage`, `system_prompt`, or `instructions` field.

4. **Command-line flag.** Some tools accept `--read`, `--instructions`, or similar flags for loading context files.

In all cases, the content is the same: your context components in plain markdown, organized by relevance to the tool's purpose.


## Cross-Platform File Management

If you use multiple AI tools on the same project, you may need several context files:

```
<project-root>/
├── CLAUDE.md                        # Claude Code
├── AGENTS.md                        # Codex, OpenCode
├── GEMINI.md                        # Gemini CLI
├── .cursorrules                     # Cursor (or .cursor/rules/)
├── .windsurfrules                   # Windsurf
├── .clinerules                      # Cline
├── .github/
│   └── copilot-instructions.md      # GitHub Copilot
└── .aider-context.md                # Aider
```

To avoid maintaining duplicate content, consider a source-of-truth approach:

1. Maintain your canonical context components in one location (e.g., `~/.context/` or your Context Stack directory)
2. Create tool-specific files that reference or paste from the canonical source
3. When you update a component, propagate the change to each tool's file

This is a manual process today. Some users write a simple script to generate tool-specific files from their canonical components.