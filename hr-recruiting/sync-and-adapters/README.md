# Sync And Adapters

> ## Cross-device sync

- Sync source files through Git: Markdown + JSONL + spec/docs.
- Rebuild SQLite locally when needed.

## Adapter model

- GitHub

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Sync and Adapter Strategy

## Cross-device sync

- Sync source files through Git: Markdown + JSONL + spec/docs.
- Rebuild SQLite locally when needed.

## Adapter model

- GitHub sync: `github-status`, `github-pull`, `github-push`, `github-bootstrap`.
- Notion: read/write mirror layer.
- Credential refs: `env://...`, `op://...`.
- R2: pre-signed upload/download.

Adapters are optional and must not break local core memory flow.