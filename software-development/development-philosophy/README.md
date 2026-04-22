# DEVELOPMENT PHILOSOPHY

> This document outlines the core philosophy and methodology used to develop and enhance the OOS project.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# The OOS Development Philosophy: Systematic Completion

This document outlines the core philosophy and methodology used to develop and enhance the OOS project. It is a guide for ensuring that all contributions result in production-ready systems, not just isolated features.

## Core Philosophy: "Systematic Completion"

The key insight is treating each request not as isolated tasks, but as complete systems that need to reach production quality.

### 1. Architectural Thinking First

Instead of just "build X", we approach it as:
- "What system does X belong to?"
- "How does X integrate with existing infrastructure?"
- "What are the real-world constraints?"

This prevents building isolated components that don't work together.

### 2. Implementation Strategy: "Build the Whole Stack"

Every feature needs its complete operational context to be truly useful. When we build a feature, we consider all layers:
- **Data layer**: Database schemas, queue systems, data formats.
- **Business logic**: Processing pipelines, core algorithms.
- **Integration layer**: Connections to other tools and systems.
- **Interface layer**: CLI commands, API endpoints.
- **Deployment layer**: Configuration, setup scripts.
- **Documentation layer**: System and user documentation.

### 3. Quality Gates as Design Constraints

Testing, linting, and deployability are not afterthoughts; they are design constraints that shape the architecture from the beginning.
- "Can this be tested?" influences architecture decisions.
- "Does this lint cleanly?" forces better code organization.
- "Can this be deployed?" shapes the interface design.

### 4. Integration-First Development

New features that integrate deeply are more valuable than standalone tools. We build new components to extend, not replace, and ensure every new component enhances the existing ecosystem.

### 5. Production Mindset Throughout

From the first line of code, we assume every component will be:
- **Running continuously**: Requires robust erro

*[truncated — see source for full prompt]*