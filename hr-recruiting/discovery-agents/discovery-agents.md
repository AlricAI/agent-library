---
name: Discovery Agents
description: How to create AI agents that lead people through building, reviewing, and updating their Context Stack on any platform.
model: claude-sonnet-4-5
---
# Discovery Agents

How to create AI agents that lead people through building, reviewing, and updating their Context Stack on any platform.

A discovery agent is not a prompt you paste and forget. It is a persistent, reusable system that interviews someone, drafts their context files, refines them through feedback, and can be returned to later for updates. This guide covers how to build that system on every major AI platform, with platform-specific optimizations that make the experience better than a raw prompt paste.


## The Discovery System

Every discovery agent, regardless of platform, needs to do five things:

1. **Orient.** Explain what the Context Stack is, what the session will produce, and how long it will take.
2. **Interview.** Ask questions one at a time, probe for specifics, and adapt based on answers.
3. **Draft.** Generate structured context files using the person's actual language.
4. **Refine.** Present drafts for correction, incorporate feedback, and check consistency across files.
5. **Hand off.** Explain what to do with the finished files: where to save them and how to load them.

The three discovery tiers handle this at different depths:

| Tier | Time | Components | Best For |
|:-----|:-----|:-----------|:---------|
| Quick Start | 5 minutes | 3 core files | First-time users, quick proof of concept |
| Guided Session | 30-45 minutes | All 12 files | Most professionals, recommended starting point |
| Deep Dive | 60-90 minutes | All 12 files + loading recommendations | Power users who want maximum precision |

The prompt for each tier is in the `discovery/` directory:
- `discovery/quick-start.md`
- `discovery/context-discovery-session.md`
- `discovery/deep-dive.md`

The update prompt for refreshing existing context is in:
- `discovery/context-update-session.md`


## Two Ways to Use the Discovery Prompts

### Option A: Paste Into a Conversation

Open any AI assistant. Paste the discovery prompt as your first message. The session starts immediately.

This works on every platform. No setup required. The trade-off: you cannot reuse the configuration, and the prompt consumes tokens from your conversation window every time.

**When to use Option A:**
- You are trying this for the first time and want to see how it works
- You are building context for yourself (one-time setup)
- Your platform does not support persistent agent creation

### Option B: Create a Reusable Discovery Agent

Build a persistent agent on your platform that runs the discovery session automatically. The prompt lives in the agent's instructions, not in the conversation. Every new conversation with the agent starts the session fresh without re-pasting.

**When to use Option B:**
- You want to run the session for multiple people (team, clients, workshop participants)
- You plan to return later for updates
- You want to share the discovery experience with others
- You want the cleanest possible conversation experience (no prompt preamble)


## Platform Guide

### Gemini (Gem)

#### Creating the Gem

1. Open [gemini.google.com](https://gemini.google.com)
2. Open **Gem Manager** (left sidebar)
3. Click **Create Gem**
4. **Name:** "Context Discovery" (or "Context Discovery: Quick Start" if you plan to create multiple tiers)
5. **Instructions:** Paste the entire prompt block from your chosen discovery tier
6. **Knowledge:** Optionally upload files or connect Google Drive documents. Gems can accept file uploads and Drive connections, making them useful for providing sample context files or reference materials.
7. **Default Tool:** Select the default tool the Gem should use (e.g., Search, Code, or none)
8. Save the Gem

#### Which Tier to Use

Gems have an instruction character limit. The Quick Start prompt fits comfortably. The Guided Session prompt fits in most cases. The Deep Dive prompt may be too long for some Gem configurations.

| Tier | Fits in Gem Instructions? | Recommendation |
|:-----|:--------------------------|:---------------|
| Quick Start | Yes | Best fit for Gems |
| Guided Session | Usually | Test it; trim the file structure examples if needed |
| Deep Dive | May exceed limit | Use Option A (paste into conversation) instead |

If the prompt is too long for Gem instructions, paste it into a regular Gemini conversation instead.

> **Note:** Google has not published an official character limit for Gem instructions. The table above reflects observed behavior. If a prompt is too long, Gemini will show an error when you save. Test before finalizing.

#### Prompting Best Practices for Gemini

- **Front-load the role definition.** Gemini Gems respond best when the first line of instructions clearly states the role: "You are a professional context architect." Place this before session rules.
- **Use numbered lists for question sequences.** Gemini follows numbered question lists reliably. The discovery prompts already do this.
- **Keep file structure templates concise.** If you hit the character limit, the first thing to trim is the output file structure templates (the markdown headers). Replace them with a one-line instruction: "Use the section headers from the Context Stack framework."
- **Avoid nesting instructions too deep.** Gemini handles two levels of structure well (Layer > Component). Three or more levels can cause the model to lose track.

#### Handling Long Sessions

Gemini Gems maintain context within a single conversation. If the conversation grows long (Guided Session or Deep Dive), the model may start to lose earlier context. Two strategies:

1. **Layer-by-layer Gems.** Create separate Gems for each layer: "Context Discovery: Self Layer", "Context Discovery: Style Layer", etc. Each Gem handles 2-5 components. The person moves between Gems.
2. **Paste-and-continue.** Run the session as a regular conversation (Option A). If context degrades, start a new conversation, paste the prompt again, paste the files generated so far, and tell the AI where you left off.

#### Creating an Update Gem

Create a second Gem named "Context Update" using the prompt from `discovery/context-update-session.md`. When the person starts a conversation with this Gem, they paste their existing context files and the Gem leads them through the update.

#### Output Handling

Gemini has limited file download capabilities. The person should ask the Gem to present each file in a separate code block for easy copy-paste. They then save each as a `.md` file manually.

---

### ChatGPT (Custom GPT)

> **Note:** Creating Custom GPTs requires a ChatGPT Plus, Team, or Enterprise subscription. Free users can use GPTs that others have shared, but cannot create their own.

#### Creating the GPT

1. Go to **Explore GPTs** (left sidebar or top menu)
2. Click **Create**
3. Go to the **Configure** tab
4. **Name:** "Context Discovery"
5. **Description:** "Builds your professional Context Stack through a structured interview. Produces 3-12 context files depending on session depth."
6. **Instructions:** Paste the entire prompt block from your chosen discovery tier
7. Optionally, upload knowledge files (see below)
8. Enable **Code Interpreter and Data Analysis** if you uploaded knowledge files (required for the GPT to process them). Optionally enable **Web Search** if you want the GPT to fact-check domain claims during the interview.
9. Add 2-3 Conversation Starters such as "Start my Context Stack discovery session" and "I want to update my existing context files."
10. Save the GPT

#### Using Knowledge Files

ChatGPT GPTs can accept uploaded knowledge files that the GPT references during conversation. This is a significant advantage over other platforms.

**Recommended knowledge files to upload:**
- 2-3 sample context-component files from the `samples/` directory. These give the GPT concrete examples of what good output looks like.
- `architecture/loading-patterns.md` so the GPT can provide loading recommendations at the end.

Do not upload all sample files. Two or three representative samples are enough to establish the pattern. Uploading too many can cause the GPT to copy example phrasing instead of using the person's own words.

> **Note:** GPTs support up to 20 knowledge files, each up to 512 MB. For discovery agents, 2-3 sample files are sufficient.

#### Which Tier to Use

Custom GPT instructions support 8,000 characters (hard limit). All three tiers fit.

| Tier | Fits in GPT Instructions? | Recommendation |
|:-----|:--------------------------|:---------------|
| Quick Start | Yes | Good for sharing with people who want a fast experience |
| Guided Session | Yes | Best default for a general-purpose discovery GPT |
| Deep Dive | Yes | Best for power users; add sample files as knowledge |

#### Prompting Best Practices for ChatGPT

- **Add explicit output formatting instructions.** ChatGPT sometimes presents drafted files inline rather than in code blocks. Add this to the end of the prompt: "Present each drafted file inside a markdown code block with the filename as a header above it."
- **Use knowledge files for few-shot examples.** Uploading 2-3 sample component files as GPT knowledge gives the model concrete patterns to follow. This produces better-structured output than relying on the prompt alone.
- **Instruct the GPT to offer file downloads.** ChatGPT can generate downloadable files. Add: "After presenting the final versions, offer to generate each file as a downloadable .md file." This saves the person from manual copy-paste.
- **Set conversation starters.** In the GPT configuration, add conversation starters like:
  - "I'm ready to build my Context Stack."
  - "I want to update my existing context files."
  - "What is the Context Stack and how does this work?"
- **Handle the memory interaction.** ChatGPT's Memory feature may store facts from the discovery session. Add to the prompt: "Do not rely on ChatGPT Memory for this session. All context should come from the person's answers, not from prior conversations."

#### Creating an Update GPT

Create a second GPT named "Context Update" using the prompt from `discovery/context-update-session.md`. Upload the person's existing context files as knowledge, or instruct them to paste the files at the start of the conversation.

Alternatively, add both the discovery and update prompts to a single GPT and include a conversation starter: "I want to update my existing context files." The GPT detects which mode to use based on whether existing files are provided.

#### Output Handling

ChatGPT can generate downloadable files. Add this instruction to the prompt: "After the person approves the final versions, generate each context file as a downloadable markdown file." The person downloads the files directly instead of copying from the chat.

---

### Claude.ai (Project)

#### Creating the Project

1. Go to [claude.ai](https://claude.ai)
2. Click **Projects** in the left sidebar
3. Click **Create a project**
4. **Name:** "Context Discovery"
5. **Description:** "Structured interview that builds your professional Context Stack."
6. In **Project instructions**, paste the entire prompt block from your chosen discovery tier
7. Optionally, upload sample files as project knowledge (see below)

> **Important:** The project name and description are not visible to Claude. Only the project instructions and uploaded knowledge files are included in Claude's context. Do not put important guidance in the description field; put it in the project instructions instead.

#### Using Project Knowledge

Claude Projects can include uploaded files as persistent knowledge. This is the best implementation of the discovery agent across all platforms.

> **Note:** Supported formats include PDF, DOCX, CSV, TXT, Markdown (.md), and plain text. Each file can be up to 30 MB. Projects are available on all Claude plans, including free accounts (limited to 5 projects).

**Recommended files to upload:**
- 2-3 sample context-component files from `samples/`. These serve as reference examples.
- `context-components/README.md` for the full component specification.
- `architecture/loading-patterns.md` for loading recommendations.

Add a note at the top of the project instructions: "The project knowledge contains sample context files and the component specification. Use these as reference for structure and depth, but write all content using the person's actual words and phrasing."

#### Which Tier to Use

Claude Projects have generous instruction capacity. All three tiers fit comfortably.

| Tier | Fits in Project Instructions? | Recommendation |
|:-----|:------------------------------|:---------------|
| Quick Start | Yes | Good for quick demonstrations |
| Guided Session | Yes | Best default |
| Deep Dive | Yes | Best for comprehensive context; upload samples as knowledge |

#### Prompting Best Practices for Claude

- **Use structured formatting.** Claude handles deeply nested instructions well. The discovery prompts' layer/component/question hierarchy works naturally with Claude's processing.
- **Leverage project knowledge for few-shot learning.** Uploading sample files produces the strongest output quality improvement of any platform. Claude genuinely reads and references the uploaded files, matching their structure and depth.
- **Separate instructions from knowledge.** Put the discovery prompt in Project Instructions. Put sample files and reference docs in Project Knowledge. Claude treats these as different types of context: instructions guide behavior, knowledge provides reference material.
- **Long sessions work well.** Claude maintains context over long conversations better than most platforms. The Deep Dive tier (60-90 minutes) runs smoothly as a single conversation in a Claude Project.
- **Ask for XML-formatted output for programmatic use.** If the person plans to process the output programmatically, add: "Wrap each file in XML tags: `<file name='professional-identity.md'>content</file>`." This makes automated extraction easier.

#### Creating an Update Project

Create a second project named "Context Update" with the update prompt from `discovery/context-update-session.md` as project instructions. Upload the person's existing context files as project knowledge. When they start a conversation, Claude already has their current context and the update process begins immediately without pasting.

This is the most seamless update experience across all platforms: the person opens the project, starts a conversation, and Claude already knows what their context says and can identify what might be stale.

#### Output Handling

On paid plans (Pro, Max, Team, Enterprise), Claude can generate downloadable `.md` files. Add this instruction to the prompt: "After the person approves the final versions, generate each context file as a downloadable markdown file." Free plan users must copy each file from the conversation and save it locally. Claude formats markdown code blocks cleanly for copy-paste in either case.

For Claude Code users, the output from the Claude.ai discovery session can be pasted directly into `context-components/` files using their editor or terminal.

---

### Microsoft Copilot

Microsoft Copilot has three integration points, each suited to different environments.

#### Copilot Studio (Enterprise)

For organizations with Microsoft 365 Copilot, Copilot Studio is the most capable option.

1. Open [copilotstudio.microsoft.com](https://copilotstudio.microsoft.com)
2. Create a new agent
3. **Name:** "Context Discovery"
4. **Instructions:** Paste the discovery prompt from your chosen tier
5. Optionally, add knowledge sources (SharePoint documents, uploaded files)
6. Publish the agent within your organization

**Enterprise considerations:**
- Copilot Studio agents can be shared across your organization. This makes them ideal for running discovery sessions for teams.
- Knowledge sources can include SharePoint sites with sample context files, org-specific terminology, and internal role definitions.
- Data residency and compliance policies apply. The discovery session captures professional context that may be considered sensitive. Consult your compliance team if needed.

**Prompting best practices for Copilot Studio:**
- **Use clear action-oriented language.** Copilot responds best to direct instructions: "Ask the following questions in order" rather than "You might consider asking."
- **Keep instructions under 4,000 characters for reliability.** Use the Quick Start or Guided Session. The Deep Dive may be too long.
- **Leverage Topics for structured flows.** Copilot Studio supports Topics (predefined conversation paths). For the highest-quality experience, create a Topic for each layer of the discovery session with trigger phrases like "Start Layer 1" and "Start Layer 2." This gives more control than a single prompt.

#### Microsoft 365 Copilot with Agent Builder

Microsoft 365 Copilot subscribers can create lightweight agents directly in the Copilot app (microsoft365.com/chat) using Agent Builder, without needing Copilot Studio.

1. Open the Copilot app and select **Create an agent** (or navigate to Agent Builder)
2. **Name:** "Context Discovery"
3. **Instructions:** Paste the discovery prompt from your chosen tier
4. Optionally, add knowledge sources (uploaded files, SharePoint)
5. Save and use the agent in your Copilot conversations

This is a simpler option than Copilot Studio, suitable for individual use. For organization-wide deployment with Topics, governance, and Power Automate integration, use Copilot Studio instead.

#### Copilot in Edge / copilot.microsoft.com (Free Consumer)

The free consumer version of Copilot does not support persistent agent creation. Use Option A (paste the prompt into a conversation).

**Best practice:** Save the discovery prompt as a text snippet in a text expander (TextExpander, Raycast, AutoHotkey, or a simple notes file). Paste it at the start of each Copilot conversation.

**Prompting best practices for consumer Copilot:**
- Use the Quick Start prompt. Consumer Copilot has tighter context windows than enterprise Copilot.
- Copilot may try to search the web during the interview. Add to the prompt: "Do not search the web during this session. All content should come from the person's answers."

#### Creating an Update Agent in Copilot Studio

Create a second agent named "Context Update" with the update prompt. Add the person's existing context files as knowledge sources. The same enterprise considerations apply.

---

### Perplexity (Space)

Perplexity Spaces are not the strongest fit for running the full discovery session, but they add unique value for research-augmented context building and updates.

#### Using Perplexity for Discovery

1. Create a new Space
2. Add custom instructions with the discovery prompt
3. Optionally, add URLs as knowledge sources. Perplexity can index web pages for reference during the session.
4. The person starts a conversation in the Space

**Where Perplexity adds value:** Perplexity can search the web during the session. This is useful when the person mentions industry-specific context, tools, or methodologies that would benefit from current data. For example, if someone says "I am learning about agentic AI frameworks," Perplexity can pull current information about those frameworks to enrich the domain-map and learning-edge components.

**Where Perplexity is weaker:** The conversational UX is optimized for search, not extended interviews. Long discovery sessions can feel awkward. Use the Quick Start prompt for Perplexity.

#### Using Perplexity for Updates

Perplexity Spaces are excellent for context updates, particularly for components that benefit from current data:

- **strategic-context.md**: Perplexity can research the person's industry to identify relevant market changes
- **tool-ecosystem.md**: Perplexity can check whether tools mentioned in the existing file have been updated, deprecated, or replaced
- **domain-map.md**: Perplexity can surface recent developments in the person's expert domains
- **learning-edge.md**: Perplexity can find current resources for the person's learning areas

Upload existing context files to the Space and use the update prompt from `discovery/context-update-session.md`.

> **Note:** File uploads to Spaces require Perplexity Pro. Free users can add URLs as knowledge sources instead.

---

### Claude Code (Slash Command or Skill)

Claude Code is the only platform where the discovery agent can save files directly to disk. This is the most automated option.

#### Creating a Discovery Command

Create a Claude Code slash command that runs the discovery session:

**File:** `<project-root>/.claude/commands/discover-context.md`

```markdown
Run an interactive Context Discovery Session. Interview me using the Quick Start
process (10 focused questions), then draft and save three context files directly
to the context-components/ directory.

Rules:
- Ask one question at a time. Wait for my answer.
- Do not editorialize between questions.
- Push for specifics when answers are vague.
- After all questions, draft the three files and present them for review.
- After I approve, save them to context-components/ as:
  - professional-identity.md
  - communication-dna.md
  - strategic-context.md

Use my actual language. Do not polish my words into corporate prose.

Read the discovery prompt from discovery/quick-start.md and follow it exactly.
If that file is not available, ask 10 questions covering: role and organization,
daily work, what people come to you for, professional origin, current chapter,
communication style, quality standards, tools, current priorities, and goals.
```

Run it with: `/project:discover-context`

For global availability across all projects, create the file in `~/.claude/commands/` instead and invoke it with `/user:discover-context`.

For the full 12-component session, create a longer command file with the Guided Session prompt from `discovery/context-discovery-session.md`.

#### Creating an Update Command

**File:** `<project-root>/.claude/commands/update-context.md`

```markdown
Read all markdown files in the context-components/ directory. For each file,
summarize what it currently says and ask me whether it is still accurate.

If a component is still accurate, skip it. If something has changed, ask me
the minimum number of questions needed to capture the update. Then save the
updated version, preserving everything that has not changed.

After all components are reviewed, check consistency across all files and flag
any contradictions.
```

Run it with: `/project:update-context`

#### Prompting Best Practices for Claude Code

- **Save files directly.** Claude Code's primary advantage is filesystem access. Always instruct the command to save files to disk rather than presenting them for manual copy-paste.
- **Read existing files before updating.** Update commands should read current files with the Read tool before asking questions. This grounds the conversation in the actual current state.
- **Use the Write tool for new files, Edit for updates.** Discovery commands that create files from scratch should use Write. Update commands should use Edit to modify only the changed sections, preserving formatting and unchanged content.
- **Keep commands focused.** A single command that handles all 12 components is harder for the model to manage than targeted commands. Consider creating per-layer commands: `discover-self`, `discover-style`, etc.

#### Global Context Discovery

For context that applies to all your projects, create commands in `~/.claude/commands/` instead of the project directory. Invoke global commands with the `/user:` prefix (e.g., `/user:discover-context`). This makes the discovery and update commands available everywhere.

> **Note:** Claude Code also supports a newer Skills format (`.claude/skills/<name>/SKILL.md`) which offers richer configuration. The commands format shown above remains fully supported and is simpler for most use cases.

---

### Cursor

Cursor is optimized for code editing, not extended interviews. However, you can set up discovery in two ways: a custom slash command (recommended for interviews) or a rule file (better for loading existing context).

#### Option A: Custom Slash Command (Recommended for Discovery)

Cursor supports custom commands stored as markdown files. Create a command that runs the discovery interview:

**File:** `<project-root>/.cursor/commands/discover-context.md`

```markdown
Run an interactive Context Discovery Session. Interview me using the Quick Start
process (10 focused questions), then draft and save three context files directly
to the context-components/ directory.

Rules:
- Ask one question at a time. Wait for my answer.
- Do not editorialize between questions.
- Push for specifics when answers are vague.
- After all questions, draft the three files and present them for review.
- After I approve, save them to context-components/ as:
  - professional-identity.md
  - communication-dna.md
  - strategic-context.md

Use my actual language. Do not polish my words into corporate prose.
```

Invoke it by typing `/discover-context` in the Cursor Agent input.

#### Option B: Rule File (For Loading Existing Context)

If you have already built your context files and want Cursor to reference them automatically during coding sessions, create a rule:

**File:** `<project-root>/.cursor/rules/load-context.mdc`

```markdown
---
description: Load personal context when working in this project
globs: context-components/**
alwaysApply: false
---

Read the files in context-components/ to understand who is working on this
project. Apply their communication style, technical depth, and domain expertise
when generating code, documentation, or explanations.
```

This rule activates when you reference files matching the glob pattern or when the AI determines it is relevant based on the description. You can also invoke it manually by typing `@load-context` in chat.

> **Note:** The older `.cursorrules` file format still works but `.cursor/rules/` with `.mdc` or `.md` files is the current recommended approach.

#### Best Practice

Cursor's strength is code context, not open-ended interviews. Use Cursor for loading and applying context (via `.cursor/rules/`), but consider running the discovery session on a conversational platform (Claude, ChatGPT, Gemini) where the interview experience is better.

---

### Codex (OpenAI CLI)

Codex is OpenAI's terminal-based coding agent (available as CLI via `npm i -g @openai/codex` and as a Mac desktop app). It follows the `AGENTS.md` pattern for persistent instructions and can save files directly to disk.

**Recommended approach:** Run the discovery session on a conversational platform. Save the output files to your project. Create an `AGENTS.md` file that loads the context for coding sessions.

If you want to run discovery in Codex:

```bash
# Launch Codex with a discovery prompt (interactive terminal session)
codex "Run a Context Discovery session. Ask me 10 questions one at a time,
then save three context files to context-components/."
```

Codex conducts the interview in the terminal and can save files directly.

#### Context Loading for Coding Sessions

Codex reads instructions from multiple levels:
- `~/.codex/instructions.md` for global personal context
- `<repo-root>/AGENTS.md` for project-level context
- Nested `AGENTS.md` files in subdirectories (closer files take precedence)
- `AGENTS.override.md` for local overrides not checked into git

After running discovery, reference your context files in `AGENTS.md` so Codex loads them automatically in every session.

---

### Aider

Aider supports persistent instructions through read-only context files (called "conventions files"). This is the mechanism for both running discovery and loading context into coding sessions.

```bash
# Run discovery with Aider using a conventions file
aider --read discovery/quick-start.md --no-auto-commits
```

Extract the prompt block from `discovery/quick-start.md` and save it as a plain text file. The `--read` flag adds it as read-only context that Aider references throughout the session.

To persist this configuration so context loads automatically, create a `.aider.conf.yml` file:

**File:** `<project-root>/.aider.conf.yml`

```yaml
read:
  - context-components/professional-identity.md
  - context-components/communication-dna.md
  - context-components/strategic-context.md
auto-commits: false
```

This loads your context files as read-only context in every Aider session. Global configuration goes in `~/.aider.conf.yml`.

Aider is better suited for code work than open-ended interviews. Use it for loading context, not building it. Run the discovery session on a conversational platform, then configure Aider to load the resulting files.


## Choosing the Right Platform for Discovery

Not every platform is equally suited to running the discovery session. Choose based on your situation:

| If You Want... | Use This Platform |
|:----------------|:------------------|
| The best overall discovery experience | Claude Project (with sample files as knowledge) |
| Downloadable output files | ChatGPT Custom GPT or Claude Project (paid plans) |
| Files saved directly to disk | Claude Code |
| Web research during the session | Perplexity Space |
| To share with your organization | Copilot Studio, ChatGPT GPT, or Gemini Gem |
| The fastest setup | Any platform, Option A (paste) |
| To run sessions for multiple people | ChatGPT GPT or Claude Project |
| Enterprise compliance requirements | Copilot Studio |

For most individuals, start with Option A on whatever platform you already use. If you want to run sessions for others or plan to update regularly, create a dedicated agent using Option B.


## Making the Agent Lead Effectively

A discovery agent should lead the conversation, not wait passively. These patterns make the interview experience smooth regardless of platform.

### Onboarding

The agent should explain the process before the first question. Add this to the beginning of any discovery prompt (the existing prompts already include a version of this):

```
Before asking the first question, briefly explain:
- What the Context Stack is (one sentence)
- How many questions you will ask
- How long the session typically takes
- What files will be produced at the end
- That you will present drafts for review before finalizing
```

### Adaptive Depth

Not everyone gives the same level of detail. The agent should adapt:

```
If the person gives detailed, specific answers: move through questions quickly.
Do not ask for elaboration when the answer is already rich.

If the person gives short or vague answers: probe once for specifics.
"Can you give me a concrete example?" If the second answer is still vague,
accept it and move on. Do not badger.
```

### Progress Tracking

For longer sessions, the agent should signal progress:

```
After completing each layer, briefly note the transition:
"We have finished [current layer]. [X] of [Y] components are done.
Moving to [next layer], which covers [purpose]."
```

### Voice Preservation

The most common complaint about AI-drafted context is that it sounds generic. Emphasize this in every discovery prompt:

```
Use my actual words and phrasing. If I say "that drives me nuts," write
"that drives me nuts," not "this is a source of frustration." Preserve
my voice exactly as I express it.
```

### Handoff

After the session, the agent should tell the person what to do with their files:

```
After presenting the final files, explain:
- Save each file as a .md file in a dedicated directory
- Load them into your AI platforms using the guides at [project URL]
- Which files to update first and how often
- How to run an update session when things change
```


## Building Update Agents

Every platform that supports a discovery agent can also support an update agent. The update prompt is in `discovery/context-update-session.md`.

### Update Agent Design

The update agent differs from the discovery agent in three ways:

1. **It reads existing context before asking questions.** The person provides their current files (by pasting or uploading), and the agent analyzes them before the first question.
2. **It skips unchanged components.** The agent confirms each component is still accurate and only digs into components the person flags as stale.
3. **It preserves voice and content from unchanged sections.** Updates modify specific sections, not entire files.

### Platform-Specific Update Strategies

| Platform | How to Provide Existing Context |
|:---------|:-------------------------------|
| Claude Project | Upload current files as project knowledge. Agent reads them automatically. |
| ChatGPT GPT | Upload current files as GPT knowledge. Or paste at conversation start. |
| Gemini Gem | Upload current files as Gem knowledge, connect them via Google Drive, or paste at the start of the conversation. |
| Copilot Studio | Add current files as knowledge sources. |
| Claude Code | Agent reads files directly from `context-components/` on disk. |
| Perplexity Space | Upload current files to the Space. |

Claude Projects and Claude Code offer the smoothest update experience because the agent can access existing files without the person pasting anything.


## Running Discovery for Teams

If you are rolling out the Context Stack across a team or organization, the discovery agent becomes a scalable tool.

### Setup

1. Create a single discovery agent on a shared platform (ChatGPT GPT with a shared link, Claude Project with team access, or Copilot Studio agent published to your org)
2. Share the agent link with team members
3. Each person runs the session independently
4. Collect the output files in a shared directory or repository

### Facilitation Tips

- **Start with the Quick Start.** A 5-minute session that produces three files is less intimidating than a 45-minute deep dive. Let people see the value before asking for the full commitment.
- **Provide a sample.** Share one completed Context Stack (from the `samples/` directory) so people understand what they are building toward. Seeing a finished product makes the interview questions feel purposeful.
- **Do not review each other's files.** Context files are personal. The value comes from each person's honest self-assessment, not from peer review or manager approval.
- **Schedule update sessions quarterly.** Set a recurring reminder for the team to run the update agent. Context that goes stale loses its value.