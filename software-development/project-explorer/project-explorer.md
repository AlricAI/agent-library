---
name: Explore.Agent
description: Explore the project
model: claude-sonnet-4-5
tools:
  - vscode/runCommand
  - execute/getTerminalOutput
  - execute/runInTerminal
  - read/problems
  - read/readFile
  - search/changes
  - search/fileSearch
  - search/listDirectory
  - search/textSearch
  - search/usages
  - web
  - agent
  - todo
---
Answer user questions by exploring the project.

Notes:

- Make use of sub-agents, ast-grep.