# Chatgpt

> How to build and load your Context Stack using ChatGPT.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ChatGPT

How to build and load your Context Stack using ChatGPT.

ChatGPT offers several ways to load persistent context, each with different tradeoffs. The most effective approach combines Custom Instructions for your core identity with Projects for deeper context.


## Step 0: Build Your Context Stack with a Custom GPT

Before you can load your Context Stack, you need to build it. You can create a Custom GPT that runs the Context Discovery Session.

1. Go to **Explore GPTs** > **Create**
2. In the **Configure** tab, paste the entire prompt block from `discovery/quick-start.md` (5 minutes, produces 3 files) or `discovery/context-discovery-session.md` (30-45 minutes, produces all 12 files) into the **Instructions** field
3. **Name:** "Context Discovery"
4. Save the GPT
5. Start a conversation with your Context Discovery GPT
6. Answer the questions. The GPT will draft your context-component files
7. Copy each drafted file and save it as a `.md` file on your computer

Alternatively, skip the GPT and paste the prompt block directly into a new ChatGPT conversation.

Once you have your context files, follow the sections below to load them into ChatGPT for daily use.

For detailed GPT configuration best practices, knowledge file strategies, and prompting tips, see `guides/discovery-agents.md`.


## Option 1: Custom Instructions

The fastest way to get started. Custom Instructions apply to every conversation across ChatGPT.

### Setup

1. Click your profile icon (bottom left)
2. Select **Settings**
3. Go to **Personalization > Custom Instructions**
4. You will see two fields:
   - **"What would you like ChatGPT to know about you?"**
   - **"How would you like ChatGPT to respond?"**

### What to Put Where

**Field 1: "What would you like ChatGPT to know about you?"**

Paste a condensed version of your professional-identity and strategic-context. You have approximately 1,500 words per field (roughly 8,000 characters), so be dense.

Example:

```
Director of Product Operati

*[truncated — see source for full prompt]*