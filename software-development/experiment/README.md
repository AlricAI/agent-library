# EXPERIMENT

> ## Hypothesis

When an AI coding agent (Claude Code) operates inside a project with noslop's quality
guardrails installed, the resulting code will be 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# noslop A/B Experiment

## Hypothesis

When an AI coding agent (Claude Code) operates inside a project with noslop's quality
guardrails installed, the resulting code will be measurably higher quality than when the
same agent performs the same task in an identical project without guardrails.

## Methodology

### Independent variable

**Presence of noslop quality infrastructure.** Two identical TypeScript calculator projects
are created from the same fixture. One receives `noslop install --pack typescript`; the
other remains bare.

### Controlled variables

| Variable | Value |
|---|---|
| Fixture source | `fixtures/typescript/` (5 source files, 7 tests, vitest/eslint/prettier/typescript) |
| Task prompt | Identical — see [task-prompt.md](task-prompt.md) |
| Model | `sonnet` (same for both) |
| Invocation | `claude -p --dangerously-skip-permissions --model sonnet --print` |
| Node version | Same runtime, same machine |
| npm dependencies | Same `package.json` devDependencies |

### Dependent variables (quality dimensions measured)

| Dimension | Tool | What it checks |
|---|---|---|
| Formatting | `npx prettier . --check` | Code style consistency |
| Linting | `npx eslint . --max-warnings=0` | Code quality rules, complexity caps |
| Type safety | `npx tsc -p tsconfig.json --noEmit` | TypeScript strict mode compliance |
| Tests pass | `npx vitest run` | Functional correctness |
| Test coverage | `npx vitest run --coverage` | How thoroughly code is tested |
| Spelling | `npx cspell "src/**/*"` | Typo-free identifiers and strings |
| Git hooks | `git config core.hooksPath` | Whether hooks enforce checks on commit |
| Quality infra | File existence checks | AGENTS.md, CI workflows, scripts, etc. |

---

## The Fixture: Calculator App

Both projects start as exact copies of `fixtures/typescript/`, a minimal calculator
application with clean separation of concerns.

### File structure

```
src/
  errors.ts          # DivisionByZeroError class
  operations.ts      # Pure fu

*[truncated — see source for full prompt]*