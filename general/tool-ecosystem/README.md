# Tool Ecosystem

> ## Why This Matters

When AI suggests a workflow, template, or integration, it needs to know what tools you actually use. Otherwise it will recommend 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Tool Ecosystem

## Why This Matters

When AI suggests a workflow, template, or integration, it needs to know what tools you actually use. Otherwise it will recommend solutions that do not fit your environment, or worse, suggest tools you have already tried and abandoned. This file prevents that friction.

## Daily Drivers

<!-- Tools you open every day. Include how you have them configured if that matters for AI context. -->

- **Jira:** Project and sprint management. We use a customized Kanban board with swim lanes by product squad. I live in the backlog refinement and roadmap views.
- **Confluence:** Documentation hub. I maintain a team wiki with decision logs, meeting notes, and process playbooks.
- **Slack:** Primary communication. I am in ~30 channels but actively monitor about 8. I use threads religiously and expect others to do the same.
- **Google Workspace:** Slides for exec presentations, Sheets for capacity planning and OKR tracking, Docs for collaborative drafts.

## AI Tools

<!-- Which AI systems you use, what you use them for, and your comfort level. This prevents AI from over-explaining things you already know. -->

- **Claude (via Claude Code):** Primary AI assistant for writing, analysis, and workflow automation. Advanced user. I use custom instructions, skills, and slash commands daily.
- **ChatGPT:** Occasional use for image generation and quick web searches. Intermediate user.
- **GitHub Copilot:** Code suggestions in VS Code for scripting tasks. I write Python and JavaScript for automation, not production software.

## Development Environment

<!-- If applicable. Skip this section entirely if you do not write code. -->

- **VS Code** with Copilot, Python, and Markdown extensions
- **Python 3.12** for data scripts and automation
- **Node.js** for tooling and document generation
- **Git/GitHub** for version control. Comfortable with branching, PRs, and CLI workflows.

## Communication Stack

<!-- Where you send and receive messages. Helps AI kn

*[truncated — see source for full prompt]*