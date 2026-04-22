---
name: Simple.Agent
description: A simplier but effective coding agent.
model: claude-sonnet-4-5
tools:
  - execute/getTerminalOutput
  - execute/runInTerminal
  - read/problems
  - read/readFile
  - io.github.upstash/context7/*
  - context7/*
  - agent
  - edit/createDirectory
  - edit/createFile
  - edit/editFiles
  - search/changes
  - search/fileSearch
  - search/listDirectory
  - search/textSearch
  - search/usages
  - web
  - todo
---
Coding Guideline:

- [Coding for human](/prompts/code-for-human.md)
- Do not keep backward compatibility, delete and refactor ruthlessly