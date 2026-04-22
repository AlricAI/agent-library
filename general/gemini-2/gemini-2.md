---
name: Gemini
description: How to build and load your Context Stack using Google Gemini.
model: claude-sonnet-4-5
---
# Google Gemini

How to build and load your Context Stack using Google Gemini.

Gemini offers three main integration points: Gems for the consumer product, system instructions in AI Studio for developers, and GEMINI.md for the Gemini CLI.


## Step 0: Build Your Context Stack with a Gem

Before you can load your Context Stack, you need to build it. The fastest way is to create a Gem that runs a Context Discovery Session.

1. Open [gemini.google.com](https://gemini.google.com)
2. Open **Gem Manager** and click **Create Gem**
3. **Name:** "Context Discovery"
4. **Instructions:** Copy the entire prompt block from `discovery/quick-start.md` (5 minutes, produces 3 files) or `discovery/context-discovery-session.md` (30-45 minutes, produces all 12 files) and paste it into the Instructions field
5. Save the Gem
6. Start a conversation with your Context Discovery Gem
7. Answer the questions. The Gem will draft your context-component files
8. Copy each drafted file and save it as a `.md` file on your computer

Once you have your context files, follow the sections below to load them into Gemini for daily use.

For detailed Gem configuration best practices, prompting strategies, and tips for handling long sessions, see `guides/discovery-agents.md`.


## Option 1: Gems (Gemini Web/App)

Gems are custom personas you create within Gemini. Each Gem has persistent instructions that apply to every conversation you start with it.

### Create a Personal Context Gem

1. Open [gemini.google.com](https://gemini.google.com)
2. Click **Gem manager** in the left sidebar (or navigate to **Settings > Gems**)
3. Click **Create Gem**

### Configure the Gem

**Name:** "My Context" (or "Personal Assistant", whatever is clear to you)

**Instructions:** Paste your context components here. Gems accept substantial instruction text, so you can include multiple components.

Recommended content for a general-purpose Gem:

```
# My Professional Context

## Professional Identity
[Paste professional-identity.md content]

## Communication DNA
[Paste communication-dna.md content]

## Strategic Context
[Paste strategic-context.md content]

## Domain Map
[Paste relevant sections from domain-map.md]
```

### Using Your Gem

Select your Gem from the Gem manager before starting a conversation. Every message in that conversation benefits from your loaded context.

You can create multiple Gems for different purposes:

| Gem | Components to Include |
|:----|:----------------------|
| "My Context" (general) | professional-identity + communication-dna + strategic-context |
| "Writing Assistant" | professional-identity + communication-dna + brand-voice |
| "Strategy Partner" | professional-identity + decision-architecture + strategic-context + domain-map |
| "Research Companion" | domain-map + learning-edge + strategic-context |

### Limitations

- Gem instructions have a character limit. If your combined context exceeds it, prioritize professional-identity and communication-dna.
- Gems support file uploads (PDF, TXT, and other formats) and Google Drive connections in addition to pasted text instructions. If your combined context exceeds the instruction character limit, upload files or connect Drive documents instead of pasting everything inline.
- Each Gem is a separate conversation space. Context does not carry between Gems.


## Option 2: Google AI Studio (System Instructions)

For developers and power users, Google AI Studio provides full control over system instructions with generous token limits.

### Setup

1. Open [aistudio.google.com](https://aistudio.google.com)
2. Click **Create new prompt** (or open an existing one)
3. Find the **System instructions** panel (left side or top of the prompt editor)

### Load Your Context

Paste your full Context Stack into the system instructions field:

```
# Professional Context

## Professional Identity
[professional-identity.md]

## Communication DNA
[communication-dna.md]

## Values and Boundaries
[values-and-boundaries.md]

## Domain Map
[domain-map.md]

## Strategic Context
[strategic-context.md]

## Decision Architecture
[decision-architecture.md]

## Collaboration Profile
[collaboration-profile.md]

## Feedback Journal
[feedback-journal.md]
```

AI Studio supports long system instructions, so you can include more components than Gems allow.

### Save as a Preset

After configuring your system instructions, save the prompt as a preset. This lets you reuse the same context configuration without re-pasting.

### Limitations

- AI Studio is a developer tool. The interface is functional, not polished.
- System instructions persist per saved prompt, not globally across all prompts.
- Requires a Google Cloud account for some features.


## Option 3: Gemini CLI (GEMINI.md)

The Gemini CLI reads context from a `GEMINI.md` file in your project root, similar to how Claude Code reads `CLAUDE.md`.

### Setup

Create a `GEMINI.md` file in your project root:

**File:** `<project-root>/GEMINI.md`

```markdown
# Project Context

## Professional Identity
[Paste professional-identity.md content]

## Communication DNA
[Paste communication-dna.md content]

## Domain Map
[Paste relevant domain-map.md sections]

## Strategic Context
[Paste strategic-context.md content]

## Tool Ecosystem
[Paste tool-ecosystem.md content]
```

### File Structure

```
<project-root>/
├── GEMINI.md           # Gemini CLI reads this automatically
├── src/
├── package.json
└── ...
```

### Recommendations

- Keep GEMINI.md focused on project-relevant context. Move personal identity content to the most concise form possible.
- If you also use Claude Code, you can maintain both `CLAUDE.md` and `GEMINI.md` with overlapping but tailored content.


## Choosing the Right Option

| Use Case | Best Option |
|:---------|:------------|
| Daily conversations and quick tasks | Gem |
| Detailed work with full context | AI Studio |
| Code and project work | Gemini CLI with GEMINI.md |

Start with a single Gem containing your Self and Style layers. Add AI Studio for work that needs your full Substance and Situation layers.


## Testing Your Setup

Start a new conversation with your Gem (or in AI Studio with your system instructions loaded) and ask:

```
Based on your instructions, describe my professional role and the
communication style I expect.
```

Then test with a real task:

```
Help me prepare talking points for a meeting with my VP about
reprioritizing Q3 deliverables.
```

The talking points should reflect your strategic context, use your communication style, and assume your domain expertise. If they sound like generic meeting prep, strengthen your professional-identity and strategic-context content.