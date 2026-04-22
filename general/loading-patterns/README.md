# Loading Patterns

> Which context components to load for different tasks.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Loading Patterns

Which context components to load for different tasks.


## The Principle

Do not load everything every time. Each context component consumes tokens from your conversation window. Loading all 12 components when you only need three wastes capacity and can dilute the AI's attention.

Instead, match your context to your task. Load the components that directly improve the interaction. Leave the rest out.

This is especially important on platforms with tight token limits (ChatGPT Custom Instructions, Gems). On platforms with generous context (Claude Projects, Claude Code), full-stack loading is fine for general-purpose use.


## Loading Profiles

### Writing and Content

When drafting emails, blog posts, presentations, internal communications, or any written output.

```
professional-identity.md      # Voice authority and perspective
communication-dna.md           # Writing patterns and anti-patterns
brand-voice.md                 # External tone and style
strategic-context.md           # Current priorities for relevant framing
```

**Why these four:** Writing quality depends on voice accuracy. The AI needs to know who you are (identity), how you write (communication-dna), how you present externally (brand-voice), and what you are working on (strategic-context) to produce drafts that sound like you and address the right topics.

### Strategic Planning

When working on roadmaps, OKRs, prioritization, resource allocation, or organizational strategy.

```
professional-identity.md       # Role authority and perspective
decision-architecture.md       # How you evaluate options and tradeoffs
strategic-context.md           # Current priorities and constraints
domain-map.md                  # What you know and where gaps exist
```

**Why these four:** Strategic work requires the AI to reason from your position (identity), apply your decision frameworks (decision-architecture), account for your current reality (strategic-context), and respect your domain bounda

*[truncated — see source for full prompt]*