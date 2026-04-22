---
name: Loading Patterns
description: Which context components to load for different tasks.
model: claude-sonnet-4-5
---
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

**Why these four:** Strategic work requires the AI to reason from your position (identity), apply your decision frameworks (decision-architecture), account for your current reality (strategic-context), and respect your domain boundaries (domain-map).

### Code and Technical Work

When writing code, reviewing architecture, debugging, or evaluating technical options.

```
tool-ecosystem.md              # Your tech stack and proficiency levels
operating-rhythm.md            # How you structure technical work
values-and-boundaries.md       # Quality standards and non-negotiables
domain-map.md                  # Technical depth by area
```

**Why these four:** Technical work needs the AI to know your stack (tool-ecosystem), your workflow preferences (operating-rhythm), your quality bar (values-and-boundaries), and which domains you are expert vs. learning in (domain-map).

### Research and Learning

When exploring new topics, evaluating trends, or going deep on an unfamiliar area.

```
domain-map.md                  # Current knowledge levels by area
learning-edge.md               # What you are actively learning
strategic-context.md           # Why this research matters now
```

**Why these three:** Research interactions benefit when the AI knows what you already understand (domain-map), what you are trying to learn (learning-edge), and why it matters to your current work (strategic-context). This prevents the AI from over-explaining things you know or under-explaining things you don't.

### Meeting Preparation

When preparing for a specific meeting: talking points, pre-reads, agendas, or follow-up summaries.

```
collaboration-profile.md       # How you work with others
strategic-context.md           # Current priorities and projects
communication-dna.md           # How you present information
```

**Why these three:** Meeting prep requires the AI to understand your interpersonal dynamics (collaboration-profile), what you are working on (strategic-context), and how you communicate in group settings (communication-dna).

### Client Communication

When drafting client-facing messages, proposals, or presentations.

```
professional-identity.md       # Your credibility and expertise
communication-dna.md           # Your writing voice
brand-voice.md                 # Your external presentation style
collaboration-profile.md       # How you manage client relationships
```

**Why these four:** Client communication must project your professional identity, match your voice, follow your brand standards, and reflect how you build and maintain relationships.

### Decision Support

When evaluating options, making a judgment call, or building a recommendation.

```
decision-architecture.md       # Your decision frameworks and tradeoffs
strategic-context.md           # Current constraints and priorities
values-and-boundaries.md       # Non-negotiable principles
domain-map.md                  # Expertise that informs the decision
```

**Why these four:** Good decision support requires the AI to apply your specific decision-making approach (decision-architecture), account for your constraints (strategic-context), respect your principles (values-and-boundaries), and leverage your domain knowledge (domain-map).

### Feedback and Review

When reviewing someone else's work, giving feedback, or evaluating output quality.

```
feedback-journal.md            # Patterns from past corrections
communication-dna.md           # How you deliver feedback
values-and-boundaries.md       # Your quality standards
```

**Why these three:** Feedback quality depends on consistency with your past corrections (feedback-journal), delivery in your natural voice (communication-dna), and alignment with your standards (values-and-boundaries).


## Always-Load Components

If you can only load one file, load `professional-identity.md`. It is the minimum viable context. It gives the AI your role, expertise, perspective, and professional arc. Everything else builds on top of this.

If you can load two, add `communication-dna.md`. Identity plus voice covers the majority of what makes AI output feel personalized.


## Component Change Frequency

Different components have different half-lives. This affects how often you need to review and update them.

### Stable (update yearly or on role change)

```
professional-identity.md       # Changes with career moves
values-and-boundaries.md       # Deepest principles, slow to shift
```

### Slow-moving (update rarely, refine occasionally)

```
communication-dna.md           # Your voice is consistent; add anti-patterns as discovered
decision-architecture.md       # Decision frameworks evolve slowly
brand-voice.md                 # Tone shifts are gradual
operating-rhythm.md            # Work patterns change with role, not often
```

### Moderate (update quarterly)

```
domain-map.md                  # Expertise grows; new domains appear
tool-ecosystem.md              # Tech stack evolves with projects
learning-edge.md               # Update as needed, at least quarterly
collaboration-profile.md       # Shifts with team dynamics; review quarterly
```

### Active (update monthly or more often)

```
strategic-context.md           # Priorities shift with business cycles
feedback-journal.md            # Add entries after significant AI interactions
```


## Platform-Specific Loading Advice

| Platform | Token Budget | Recommendation |
|:---------|:-------------|:---------------|
| Claude Code | Generous | Full stack in global + project CLAUDE.md |
| Claude Projects | Generous | Upload all 12 components |
| ChatGPT Custom Instructions | ~1,500 chars per field | Condensed identity + style only |
| ChatGPT Projects | Moderate | 4 to 8 components by purpose |
| Gemini Gems | Moderate | 3 to 5 components by purpose |
| Google AI Studio | Generous | Full stack in system instructions |
| Perplexity Spaces | Moderate | Research-relevant components only |
| Cursor / Codex / Other IDEs | Moderate | Technical components + condensed identity |