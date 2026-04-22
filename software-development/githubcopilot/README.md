# GitHubCopilot

> This repository is a dev framework that currently uses Claude Code to provide a text based agentic ai development environment.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Enabling amplihack to use GitHub Copilot Copilot

This repository is a dev framework that currently uses Claude Code to provide a text based agentic ai development environment.

We would lke to enahce it to also be able to use GitHub Copilot CLI.

First, You should learn about how Claude Code works - in particular it has use of valuable feature called subagents, hooks, and commands. You should read about them in detail here: @https://docs.claude.com/en/docs/claude-code/overview and the pages that it links to for those topics.

The power of this project lies in its instructions in @CLAUDE.md, and the various subagents (in @~/.amplihack/.claude/agents/_/_.md), commands (in @~/.amplihack/.claude/commands/\*), hooks (configured in .claude/settings.json and run from .claude/tools/)

The CLAUDE.md and other files reference context in the @~/.amplihack/.claude/context directory, especially the @~/.amplihack/.claude/context/PHILOSOPHY.md. This is a very important document for guiding code generation and planning.

All code changes must follow specific workflows. The default workflow is in @~/.amplihack/.claude/workflows/DEFAULT_WORKFLOW.md.

This project is run using a cli "amplihack" which is in @src/

`amplihack launch` launches the interactive text ui.

`amplihack launch -- -p <prompt>` passes a prompt to claude code.

Our objective in this session is to adapt these tools to work with The GitHub Copilot CLI (@https://docs.github.com/en/copilot/how-tos/use-copilot-agents/use-copilot-cli - these docs mostly cover the interactive use - run `coplot --help` to see the non-interactive use).

What we will do is create prompts and automation that let us leverage amplihack to drive the GH Copilot CLI. We are also going to create a special "copilot --auto" mode that creates and agentic loop around copilot cli prompts.

## New amplihack commands

You will build thee new commands:

`amplihack claude` - launch claude code - exactly as dos today with "amplihack launch" -

`amplihack

*[truncated — see source for full prompt]*