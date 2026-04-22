# SKILL Llm Code Docs Writer

> This file documents the path conventions and workflow for the `llm-code-docs` Claude skill.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# llm-code-docs-writer Skill Reference

This file documents the path conventions and workflow for the `llm-code-docs` Claude skill.
It is a copy of the skill reference committed to the repo for discoverability.

Source of truth: `~/.claude/skills/llm-code-docs/` (symlinked from `~/gitea/jset/claude/skills/llm-code-docs/`)

---

## Repository Structure

Docs use a **library-centric** layout: `docs/{lib}/{source-type}/`

```
~/github/llm-code-docs/
├── docs/
│   └── {lib}/           # One directory per library
│       ├── llms/        # llms.txt content (HIGHEST PRIORITY)
│       ├── github/      # GitHub repo /docs extractions
│       ├── web/         # Custom scrapers (last resort)
│       ├── docs-rs/     # Rust crates (docs.rs)
│       ├── hexdocs/     # Elixir/Erlang (hexdocs.pm)
│       ├── go-native/   # Go modules (gomarkdoc)
│       ├── pkg-go-dev/  # Go packages (pkg.go.dev)
│       ├── readthedocs/ # Python (ReadTheDocs epub)
│       ├── rubydoc/     # Ruby gems (rubydoc.info)
│       └── javadoc/     # Java/JVM (javadoc.io)
├── scripts/             # Extraction and update tools
└── index.yaml           # Index of all sources
```

## Source Types

| Source Type | Target Directory | When to Use |
|------------|-----------------|-------------|
| `llms` | `docs/<name>/llms/` | Library has llms.txt — highest quality |
| `github` | `docs/<name>/github/` | GitHub repo with /docs folder |
| `docs-rs` | `docs/<name>/docs-rs/` | Rust crate on crates.io |
| `hexdocs` | `docs/<name>/hexdocs/` | Elixir/Erlang package on hex.pm |
| `go-native` | `docs/<name>/go-native/` | Go module (via gomarkdoc) |
| `pkg-go-dev` | `docs/<name>/pkg-go-dev/` | Go package (pkg.go.dev) |
| `readthedocs` | `docs/<name>/readthedocs/` | Python project on ReadTheDocs |
| `rubydoc` | `docs/<name>/rubydoc/` | Ruby gem (rubydoc.info) |
| `javadoc` | `docs/<name>/javadoc/` | Java/JVM library (javadoc.io) |
| `web` | `docs/<name>/web/` | Custom scraper — last resort |

## Workflow Summary

1. Chec

*[truncated — see source for full prompt]*