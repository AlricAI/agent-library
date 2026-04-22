# Operational Rules

> These rules apply to **all providers** (Claude, Gemini, Codex/GPT) when working on this project.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Operational Rules

These rules apply to **all providers** (Claude, Gemini, Codex/GPT) when working on this project.

---

## Applying to Jobs — Standing Orders

When the user asks to apply to one or more jobs (via CLI, TUI, or directly), follow these rules without prompting:

1. **Default to `--draft`.** "Apply" means generate materials and fill the application form, but stop before submitting. Present the draft to the user and only submit with `--submit` after explicit approval. If the user explicitly says "submit" or "auto-submit", skip the draft review and use `--submit` directly.
2. **Resolve JD from application URLs.** If given a direct application link with no JD, derive the JD URL from the URL structure or career site.
3. **Unsupported boards → build support.** If the job board isn't supported, implement it following the existing autofill architecture.
4. **Blockers → log and move on.** For captchas, account locks, or questions with very low confidence: log to `submit/manual_review.json` with the issue, context, and resolution suggestions. Then continue to the next job.
5. **Low-confidence answers → best guess + log.** For questions where you have some confidence but aren't sure, fill your best answer and log it to `submit/manual_review.json` with your reasoning and alternatives.

---

## Approval Boundaries

Use the risk tiers in [`harness-governance.md`](harness-governance.md).

- `L0`: repo-local docs, tests, and verification with no external side effects
- `L1`: local runtime settings, imported user materials, and provider credentials
- `L2`: draft-mode automation and reversible browser work
- `L3`: live submission, destructive operations, push, merge, or public release

The pipeline defaults to `L2`. It must stop before any `L3` boundary unless
the user explicitly approves that action.

---

## Post-Fix Workflow — Mandatory After Every Fix

Every fix must go through ALL of these steps, no exceptions:

1. **Generalize across all boards and runtimes** — 

*[truncated — see source for full prompt]*