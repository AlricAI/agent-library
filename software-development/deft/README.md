# deft

> Apply deft framework standards for AI-assisted development. Use when starting projects, writing code, running tests, making commits, or when the user references deft, project standards, or coding guidelines.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Deft Framework

A layered framework for AI-assisted development with consistent standards and workflows.

## When This Skill Activates

This skill automatically loads when you:
- Start work in a deft-enabled project (has `./deft/` directory)
- Reference deft, project standards, or coding conventions
- Run tests, make commits, or perform quality checks
- Ask about project structure, workflows, or best practices

## Missing Config Auto-Setup

! When this skill activates, check for USER.md at the platform-appropriate path
(Windows: `%APPDATA%\deft\USER.md`, Unix: `~/.config/deft/USER.md`, or `$DEFT_USER_PATH`).

**If USER.md is missing**: Skip everything else in this file. Ask this question immediately
as your FIRST and ONLY response — no summary, no menu, no preamble:

> Deft has solid opinions on how code should be written and tested — I just need
> a few things about you and your project. First, how deep do you want to go?
>
> 1. **I'm technical — ask me everything**
> 2. **I have some opinions but keep it simple**
> 3. **Just pick good defaults — I care about the product, not the tools**

Then continue with `skills/deft-setup/SKILL.md` Phase 1 for remaining questions.

**If USER.md exists but PROJECT.md is missing at the project root**: Skip to
`skills/deft-setup/SKILL.md` Phase 2.

**If USER.md and PROJECT.md both exist but no SPECIFICATION.md at the project root**:
Skip to `skills/deft-setup/SKILL.md` Phase 3. Start the specification interview
immediately — ask what to build and features as the first question.

### ⊗ Project Root vs Framework Internals

! When checking for project-level files (`PROJECT.md`, `SPECIFICATION.md`, `PRD.md`,
`specs/`), ONLY look at the **project root** and its direct subdirectories.

- ! `./PROJECT.md` — the user's project config (project root)
- ! `./SPECIFICATION.md` or `./specs/*/SPECIFICATION.md` — the user's project spec
- ⊗ Count ANY file inside `./deft/` as a project-level artifact — those are
  framework-internal (e.g. `deft

*[truncated — see source for full prompt]*