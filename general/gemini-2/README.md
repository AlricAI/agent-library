# Gemini

> How to build and load your Context Stack using Google Gemini.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
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
[Paste professional-identit

*[truncated — see source for full prompt]*