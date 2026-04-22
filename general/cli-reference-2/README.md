# Cli Reference

> Prefer the installed CLI commands over raw `.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CLI Reference

Prefer the installed CLI commands over raw `./script.sh` invocations when working locally. The shell-script entrypoints remain valid, but they are implementation details now.

Primary commands:

```bash
# Single job end-to-end, review by default
job-assets <jd_source>
job-assets --submit <jd_source>

# Explicit subcommands
job-assets apply <jd_source> [company] [role-slug]
job-assets pipeline <jd_source> [company] [role-slug] [--submit]
job-assets submit output/<company>/<role-slug> [--submit]
job-assets batch [--dry-run] [--max-parallel N] [--provider gemini|gemini-flash|claude|codex|openai]
job-assets parallel [--dry-run] [--build-only] [--max-parallel N] [--provider gemini|gemini-flash|claude|codex|openai]
job-assets profile [show|path]
job-assets settings show
job-assets settings import <master_resume|work_stories|candidate_context|application_profile> [--file PATH|--url URL|--text TEXT]
job-assets settings set [--default-provider ...] [--openai-api-key ...] [--gemini-api-key ...]
job-assets notion-sync <target> [--wait-for-email N]

# Provider-specific wrappers
job-assets-codex <jd_source>
job-assets-claude <jd_source>
job-assets-codex --submit <jd_source>
job-assets-codex parallel --max-parallel 8
job-assets-claude batch --dry-run
```

Command discovery:
- Use `job-assets --help` for the top-level command list
- Use `job-assets apply --help`, `job-assets pipeline --help`, `job-assets submit --help`, `job-assets batch --help`, `job-assets parallel --help`, or `job-assets notion-sync --help` for subcommand details
- Use `man job-assets`, `man job-assets-codex`, or `man job-assets-claude` for manual pages after installation

## Provider Guidance

- Five providers are supported: `gemini`, `gemini-flash`, `claude`, `codex`, and `openai`. The canonical list is `VALID_PROVIDERS` in `scripts/llm_provider.py` — all CLI entrypoints import from it so provider choices stay in sync.
- `gemini` targets `gemini-3-flash-preview` by default; `gemini-flash` tar

*[truncated — see source for full prompt]*