---
name: Claude Code
description: How to load your Context Stack into Claude Code (the CLI agent).
model: claude-sonnet-4-5
---
# Claude Code

How to load your Context Stack into Claude Code (the CLI agent).

Claude Code is the deepest integration point for your Context Stack. It reads markdown files automatically at session start, with no manual copy-paste required. Your context is always present, always active.


## How Context Loading Works

Claude Code reads context from three locations, in this order:

1. **Global context** (`~/.claude/CLAUDE.md`): Loaded in every session, regardless of project
2. **Project context** (`CLAUDE.md` in your project root): Loaded when you run Claude Code from that directory
3. **Memory files** (`~/.claude/projects/<project-path>/memory/MEMORY.md`): Persistent per-project memory with an index that points to individual memory files

All three are plain markdown. No special syntax required.


## Recommended Setup

### Global CLAUDE.md: Your Self Layer

Put Self and Style components in your global file. These apply to every project and rarely change.

**File:** `~/.claude/CLAUDE.md`

```markdown
# About Me

## Professional Identity
<!-- Paste your professional-identity.md content here -->

## Communication DNA
<!-- Paste your communication-dna.md content here -->

## Values and Boundaries
<!-- Paste your values-and-boundaries.md content here -->

## Operating Rhythm
<!-- Paste your operating-rhythm.md content here -->

## Decision Architecture
<!-- Paste your decision-architecture.md content here -->
```

**What this gives you:** Every Claude Code session starts with your Self and Style layers loaded: your professional identity, communication patterns, values, and decision frameworks.

### Project CLAUDE.md: Your Substance and Situation Layers

Put Substance and Situation components in each project's context file. These vary by project.

**File:** `<project-root>/CLAUDE.md`

```markdown
# Project Context

## Strategic Context
<!-- Paste your strategic-context.md content here, filtered to this project -->

## Domain Map
<!-- Paste relevant sections from your domain-map.md -->

## Tool Ecosystem
<!-- Paste relevant sections from your tool-ecosystem.md -->

## Brand Voice
<!-- If this project involves writing, paste brand-voice.md -->
```

**What this gives you:** When working in this project, Claude Code has your Substance and Situation layers: strategic context, domain map, and tool ecosystem.

### Memory Directory: Your Synthesis Layer

Claude Code maintains a memory directory per project. Use this for your Synthesis layer: feedback-journal and learning-edge content.

**Directory:** `~/.claude/projects/<project-path>/memory/`

The `MEMORY.md` file in this directory serves as an index. Individual memory entries are stored as separate files and referenced from the index.

**Example structure:**

```
~/.claude/projects/-Users-jordan-work-api-platform/memory/
├── MEMORY.md                           # Index file
├── feedback_api_naming_conventions.md  # Specific feedback entry
├── feedback_error_message_style.md     # Another feedback entry
└── reference_deployment_process.md     # Reference information
```

**Example MEMORY.md:**

```markdown
# Project Memory

## Feedback
- [feedback_api_naming_conventions.md](feedback_api_naming_conventions.md) - Use snake_case for API fields, camelCase for internal code
- [feedback_error_message_style.md](feedback_error_message_style.md) - Error messages should state what went wrong, then what to do

## Reference
- [reference_deployment_process.md](reference_deployment_process.md) - Staging deploy requires VPN; production uses CI/CD only
```

Memory entries accumulate over time. After any interaction where you corrected Claude Code or discovered a preference worth preserving, add an entry. This is your feedback-journal in action.


## File Structure at a Glance

```
~/.claude/
├── CLAUDE.md                    # Global: identity, style, values
├── settings.json                # Preferences and tool permissions
└── projects/
    └── <project-path>/
        └── memory/
            ├── MEMORY.md        # Memory index
            └── *.md             # Individual memory entries

<project-root>/
└── CLAUDE.md                    # Project: strategy, domain, tools
```


## Settings File

Claude Code also reads `~/.claude/settings.json` for operational preferences such as tool permissions, environment variables, and other runtime configuration. This is not where context components go, but it complements them. Context and personality belong in CLAUDE.md files; settings.json handles operational behavior like which tools are allowed to run without confirmation.


## Token Budget Considerations

Claude Code has a generous context window, but it is not infinite. Each file you load consumes tokens.

- **Global CLAUDE.md**: Keep under 2,000 words. This loads every session.
- **Project CLAUDE.md**: Keep under 3,000 words. Include only project-relevant context.
- **Memory entries**: These are loaded selectively by Claude Code based on relevance.

If your global CLAUDE.md grows beyond 2,000 words, move less frequently referenced content (like collaboration-profile or brand-voice) into the project-level file for projects that need it.


## Testing Your Setup

After creating your files, start a new Claude Code session and ask:

```
Describe me based on the context you have loaded.
```

If the description misses key aspects of your identity, check that:
- Your global CLAUDE.md is at `~/.claude/CLAUDE.md` (not a subdirectory)
- Your project CLAUDE.md is in the project root (not a subdirectory)
- Content is plain markdown with clear headers

Then ask Claude Code to draft something you would normally write (an email, a code review comment, a planning document) and evaluate whether it sounds like you.


## Tips

- **Do not duplicate context.** If something is in global CLAUDE.md, do not repeat it in project CLAUDE.md.
- **Use headers to organize.** Claude Code parses markdown structure. Clear `##` headers help it find relevant context quickly.
- **Update memory actively.** After correcting Claude Code on style, terminology, or approach, add a memory entry. This compounds over time.
- **Project CLAUDE.md can be committed.** If your team shares context standards, the project-level file can live in version control. Keep personal preferences in global CLAUDE.md or memory.