# AGENTS

> > See [root AGENTS.md](.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AGENTS.md - Documentation

> See [root AGENTS.md](../AGENTS.md) for project-wide commands and guidelines.

## Overview

Infrahub documentation is organized using the [Diataxis framework](https://diataxis.fr/), separating documentation into four categories:

- **Tutorials** - Learning-oriented walkthroughs
- **Guides** - Task-oriented how-to documentation
- **Topics** - Understanding-oriented explanations
- **Reference** - Information-oriented specifications

## Before You Start

**Choose the right documentation type:**

| Question | Doc Type | See Guide |
|----------|----------|-----------|
| Teaching users to complete a specific task? | **Guide** | [guides/AGENTS.md](docs/guides/AGENTS.md) |
| Explaining concepts or how something works? | **Topic** | [topics/AGENTS.md](docs/topics/AGENTS.md) |
| Providing reference information? | **Reference** | Auto-generated |
| Walking through a complete learning scenario? | **Tutorial** | Diataxis framework |

## File Structure

- `docs/` – MDX content
  - `guides/` – How-to guides (task-oriented)
    - `AGENTS.md` – **Specialized instructions for writing guides**
  - `topics/` – Explanations (understanding-oriented)
    - `AGENTS.md` – **Specialized instructions for writing topics**
  - `reference/` – API/configuration reference
  - `tutorials/` – Learning tutorials
  - `media/` – Images and screenshots
  - `development/` – Developer documentation
    - `docs.mdx` – Documentation guide with linting rules
    - `style-guide.mdx` – **Writing style and terminology rules**
- `sidebars.ts` – Navigation configuration

## Commands

```bash
# Linting & Validation
uv run invoke docs.lint          # Run all linters (Vale + markdownlint)

# Development
uv run invoke docs.build         # Build documentation site
uv run invoke docs.serve         # Serve documentation site

# Format
uv run invoke docs.format        # Auto-format markdown files
```

## Target Audience

- **Primary:** Automation engineers, network operators, infrastructure 

*[truncated — see source for full prompt]*